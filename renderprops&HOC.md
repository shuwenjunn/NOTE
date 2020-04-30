# render props  和高阶组件

## Render Props

```js
// https://codepen.io/tudou/full/dmawvY
const Bar = ({ title }) => (<p>{title}</p>);

class Foo extends React.Component {
  constructor(props) {
    super(props);
    this.state = { title: '我是一个state的属性' };
  }
  render() {
    const { render } = this.props;
    const { title } = this.state;
    
    return (
      <div>
        {render(title)}
      </div>
    )
  }
}

class App extends React.Component {
  render() {
    return (
      <div>
        <h2>这是一个示例组件</h2>
        <Foo render={(title) => <Bar title={title} />} />
      </div>
    );
  }
}
ReactDOM.render(<App />, document.getElementById('app'))

```

在上面的例子中，给`Foo 组件`传递了一个`render`参数它是一个函数这个函数返回一个`Bar`组件，这个函数接受一个参数`title`他来自于`Foo 组件`调用时传递并且我们又将`title 属性`传递给了`Bar 组件`。经过上述的调用过程我们的`Bar 组件`就可以共享到`Foo 组件内部的`state 属性`。

## HOC

> https://juejin.im/post/5cad39b3f265da03502b1c0a#heading-8

HOC增强组件，是设计模式中装饰器模式的实现

```javascript
function proxyHoc(WrappedComponent) {
  return class extends Component {
    constructor(props) {
      super(props);
      this.state = { value: '' };
    }

    onChange = (event) => {
      const { onChange } = this.props;
      this.setState({
        value: event.target.value,
      }, () => {
        if(typeof onChange ==='function'){
          onChange(event);
        }
      })
    }

    render() {
      const newProps = {
        value: this.state.value,
        onChange: this.onChange,
      }
      return <WrappedComponent {...this.props} {...newProps} />;
    }
  }
}

class HOC extends Component {
  render() {
    return <input {...this.props}></input>
  }
}

export default proxyHoc(HOC);

```

## hooks

> https://juejin.im/post/5be3ea136fb9a049f9121014#heading-9
>
> https://juejin.im/post/5dbbdbd5f265da4d4b5fe57d#heading-1

###  useContext

```javascript
const stateContext = createContext('default');
const ContextComponent = () => {
  	const value = useContext(stateContext);
    return (
        <>
            <h1>{value}</h1>
        </>
    );
}
export default () => (
    <stateContext.Provider
        value={"Hello React"}
    >
        <ContextComponent/>
    </stateContext.Provider>
)

```

