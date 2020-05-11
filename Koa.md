# Koa 

> https://www.colabug.com/2019/1225/6769705/amp/
>
> https://juejin.im/post/5be3a0a65188256ccc192a87#heading-8
>
> https://github.com/chenshenhai/koajs-design-note

```js
const app = function () {
    // 中间件公共的处理数据
    let context = {}
    // 中间件队列
    let middlewares = []
    return {
        // 将中间件放入队列中
        use(fn) {
            middlewares.push(fn)
        },
        // 调用中间件
        callback() {
            // 初始调用 middlewares 队列中的第 1 个中间件
            return dispatch(0)
            function dispatch(i) {
                // 获取要执行的中间件函数
                let fn = middlewares[i]
                // 执行中间件函数，回调参数是：公共数据、调用下一个中间件函数
                // 返回一个 Promise 实例
                return Promise.resolve(
                    fn(context, function next() { dispatch(i + 1) })
                )
            }
        },
    }
}

app.use(async (ctx, next)=>{
    console.log(1)
    // await next();
    console.log(1)
});
app.use(async (ctx, next) => {
    console.log(2)
    // await next();
    console.log(2)
})
app.use(async (ctx, next) => {
    console.log(3)
})
```

