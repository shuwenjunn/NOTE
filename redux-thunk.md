Rudux-thunk & Redux-saga

参考文章：[Redux中发送异步请求及Redux中的React-thunk中间件使用](https://blog.csdn.net/qq_38277366/article/details/82927331)

https://blog.csdn.net/xutongbao/article/details/93765735

redux-thunk是一个redux的中间件，用来处理redux中的复杂逻辑，比如异步请求。

`redux-thunk`中间件可以让`action`创建函数先不返回一个`action`对象，而是返回一个函数。

`redux-saga` 出发点跟 `redux-thunk` 是一样的，为了解决异步操作，把异步的逻辑单独的放到一个`saga.js`文件里面。 采用的是 `generator` 函数进行构建的。[国内文档](https://redux-saga-in-chinese.js.org/docs/introduction/BeginnerTutorial.html)。

本文链接：[react中间件 react-saga](https://blog.csdn.net/qq_35962128/article/details/82494747)

https://blog.csdn.net/gao_xu_520/article/details/80527421





React 中的this

Bind call apply

