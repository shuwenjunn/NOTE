# render props  和高阶组件

高阶组件(HOC)

高阶组件和 react-redux有相应的关系

参考[React 进阶之高阶组件](!https://juejin.im/post/595243d96fb9a06bbd6f5ccd)

### ref



react class 中的this指向问题





### Render Props



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