#  reduce

## 一、语法

```javascript
  arr.reduce(function(prev,cur,index,arr) {
      ...
    },init)
    //arr 表示原数组；
    //prev 表示上一次调用回调时的返回值，或者初始值 init;
    //cur 表示当前正在处理的数组元素；
    //index 表示当前正在处理的数组元素的索引，若提供 init 值，则索引为0，否则索引为1；
    //init 表示初始值
```

## 二、使用

```javascript
    var arr=[1,2,3,4,5,5]

    //数组求和
    var sum=arr.reduce(function(prev,cur) {
      return prev+cur
    },0)
    //说明：由于传入了初始值0，所以开始时prev的值为0，cur的值为数组第一项1，相加之后返回值为3作为下一轮回调的prev值，然后再继续与下一个数组项相加，以此类推，直至完成所有数组项的和并返回。

    //求数组最大值
    var max = arr.reduce(function (prev, cur) {
        return Math.max(prev,cur)
    })
    //说明：由于未传入初始值，所以开始时prev的值为数组第一项1，cur的值为数组第二项9，取两值最大值后继续进入下一轮回调。

    //数组去重
    var newArr = arr.reduce(function (prev, cur) {
        prev.indexOf(cur) === -1 && prev.push(cur);
        return prev;
    },[])
    //说明：初始值为空数组，将需要去重处理的数组中的第1项在初始化数组中查找，如果找不到（空数组中肯定找不到），就将该项添加到初始化数组中。依次执行...最后将去重的数组返回。
```

