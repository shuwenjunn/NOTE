# JavaScript数组方法速查手册极简版


## 1 数组属性

### 1.1 length-长度属性

每个数组都有一个length属性。针对稠密数组，length属性值代表数组中元素的个数。当数组是稀疏数组时，length属性值大于元素的个数。

```
var array1 = [ 'a', 'b', 'c' ];  
console.log(array1.length);  // 输出 3
array1.length = 2;
console.log(array1);  // 输出 [ "a", "b" ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/length)

## 2 数组方法

### 2.1 Array.isArray-类型判定

`Array.isArray()` 数组类型判定。

```
console.log(Array.isArray([1, 2, 3]));   // 输出 true
console.log(Array.isArray({num: 123}));   //输出 false

```

[查看示例程序](http://30ke.cn/code/js-array-method/isArray)

### 2.2 Array.of-创建数组

`Array.of()` 从可变数量的参数创建数组，不管参数的数量或类型如何。

```
console.log(Array.of(3));    // 输出 [3]
console.log(Array.of(1,2,3));   // 输出 [1,2,3]

```

[查看示例程序](http://30ke.cn/code/js-array-method/of)

### 2.3 Array.from-创建数组

`Array.from()`  用类数组或可迭代对象创建新数组。

```
console.log(Array.from('abcd'));  // 输出 [ "a", "b", "c", "d" ]
console.log(Array.from([1, 2, 3], x => x + 1));  // 输出 [ 2, 3, 4 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/from)

## 3 数组原型方法

### 3.1 查找元素

#### 3.1.1 find-按函数查找

`Array.prototype.find()`  找到第一个满足检测函数条件的元素，并返回该元素，没找到则返回 undefined。

```
var array1 = [1, 2, 3, 4, 5];
console.log(array1.find(x => x > 3));    // 输出  4

```

[查看示例程序](http://30ke.cn/code/js-array-method/find)

#### 3.1.2 findIndex-按函数查找

`Array.prototype.findIndex()` 找到第一个满足检测函数条件的元素，并返回该元素索引。找不到返回-1。

```
var array1 = [6, 7, 8, 9, 10];
console.log(array1.findIndex(x => x > 8));    // 输出  3

```

[查看示例程序](http://30ke.cn/code/js-array-method/findIndex)

#### 3.1.3 indexOf-按元素值查找

`Array.prototype.indexOf()`  查找元素并返回元素索引值，找不到返回-1。

```
var arr= [1, 2, 3, 4];
console.log(arr.indexOf(3));    // 输出 2
console.log(arr.indexOf(6));    // 输出 -1
console.log(arr.indexOf(2, 2));    // 输出 -1

```

第二个参数表示查找的起始位置。

[查看示例程序](http://30ke.cn/code/js-array-method/indexOf)

#### 3.1.4 lastIndexOf-按元素值查找

`Array.prototype.lastIndexOf()`  从后向前查找元素并返回元素索引值，找不到返回 -1。

```
var arr = ['a', 'b', 'c', 'd'];
console.log(arr.lastIndexOf('b'));    // 输出 1
console.log(arr.lastIndexOf('e'));    // 输出 -1

```

[查看示例程序](http://30ke.cn/code/js-array-method/lastIndexOf)

### 3.2 添加元素

#### 3.2.1 push-尾部添加

`Array.prototype.push()`  在尾部添加一个或多个元素，返回数组的新长度。

```
var array1= ['a', 'b', 'c'];
console.log(array1.push('d'));   // 输出 4
console.log(array1);   // 输出 [ "a", "b", "c", "d" ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/push)

#### 3.2.2 unshift-头部添加

`Array.prototype.unshift()`  在头部添加一个或多个元素，并返回数组的新长度。

```
var array1 = [ 4, 5, 6 ];
console.log(array1.unshift(3));    // 输出 4
console.log(array1);    // 输出 [ 3, 4, 5, 6 ]
console.log(array1.unshift(1, 2));    // 输出 6
console.log(array1);    // 输出 [ 1, 2, 3, 4, 5, 6 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/unshift)

### 3.3 删除元素

#### 3.3.1 pop-尾部删除

`Array.prototype.pop()`  从尾部删除一个元素，并返回该元素。

```
var array1= ['a', 'b', 'c', 'd'];
console.log(array1.pop());    // 输出 d
console.log(array1);    // 输出 [ "a", "b", "c" ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/pop)

#### 3.3.2 shift-头部删除

`Array.prototype.shift()`  从头部删除一个元素，并返回该元素。

```
var array1 = [1, 2, 3];
console.log(array1.shift());    // 输出 1
console.log(array1);    // 输出 [ 2, 3 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/shift)

### 3.4 替换元素

#### 3.4.1 splice-添加替换删除

`Array.prototype.splice()` 添加、替换、删除元素。会改变原数组。

```
var array1 = [ 'a', 'c', 'd' ];
array1.splice( 1, 0, 'b');
console.log(array1);    // 输出 [ "a", "b", "c", "d" ]
array1.splice(1,1);
console.log(array1);    // 输出 [ "a", "c", "d" ]
array1.splice(1,1,'bb','cc');
console.log(array1);    // 输出 [ "a", "bb", "cc", "d" ]

```

> ```
> array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
> ```

- 参数 `start`：表示替换的位置
- 参数 `deleteCount` ：表示删除元素的数量
- 参数 `item1...` ： 表示添加的元素

[查看示例程序](http://30ke.cn/code/js-array-method/splice)

### 3.5 顺序相关

#### 3.5.1 sort-排序

`Array.prototype.sort()` 数组排序，改变原数组。

```
var array1 = [ 4, 3, 10, 2 ];
console.log(array1.sort());    // 输出 [ 10, 2, 3, 4 ]
console.log(array1.sort((x1, x2) => x1 > x2));    // 输出 [ 2, 3, 4, 10 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/sort)

#### 3.5.2 reverse-反序

`Array.prototype.reverse()`  倒置数组，并返回新数组。会改变原数组。

```
var sourceArray= [ 'a', 'b', 'c' ];
var reverseArray = sourceArray.reverse();
console.log(reverseArray);    // 输出 [ "c", "b", "a" ]
console.log(sourceArray == reverseArray);    // 输出 true

```

[查看示例程序](http://30ke.cn/code/js-array-method/reverse)

### 3.6 遍历迭代

#### 3.6.1 keys-键迭代器

`Array.prototype.keys()` 数组的键迭代器。

```
var array1 = ['a', 'b', 'c'];
for (let key of array1.keys()) {
  console.log(key);     // 输出 0, 1, 2
}

```

[查看示例程序](http://30ke.cn/code/js-array-method/keys)

#### 3.6.2 values-值迭代器

`Array.prototype.values()`  数组的值迭代器。

```
const array1 = ['a', 'b', 'c'];
const iterator = array1.values();
for (const value of iterator) {
  console.log(value);     // 输出 a b c
}

```

[查看示例程序](http://30ke.cn/code/js-array-method/values)

#### 3.6.3 entries-键/值对迭代器

`Array.prototype.entries()`  数组的键/值对迭代器。

```
var array1 = ['a', 'b', 'c'];
var iterator1 = array1.entries();
console.log(iterator1.next().value);    // 输出 Array [0, "a"]
console.log(iterator1.next().value);    // 输出 Array [ 1, "b" ] 

```

[查看示例程序](http://30ke.cn/code/js-array-method/entries)

#### 3.6.4 forEach-遍历

`Array.prototype.forEach()` 遍历数组中的元素，并执行回调函数。

```
var arr = [1, 2, 3, 4];
arr.forEach(function (x) {
    console.log(x + 1);    // 输出 2  3  4  5
});    

```

[查看示例程序](http://30ke.cn/code/js-array-method/forEach)

### 3.7 检测

#### 3.7.1 includes-值包含检测

`Array.prototype.includes()`  值包含检测，如包含返回 true，不包含返回false。

```
var array1 = [1, 2, 3];
console.log(array1.includes(2));    // 输出 true
console.log(array1.includes(4));    // 输出 false

```

[查看示例程序](http://30ke.cn/code/js-array-method/includes)

#### 3.7.2 some-函数包含检测

`Array.prototype.some()`  检测数组中是否有元素可以通过检测函数验证。

```js
var array1 = [ 1, 2, 3, 4 ];
console.log(array1.some(x => x >3));    // 输出  true
console.log(array1.some(x => x > 5));    // 输出  false

```

[查看示例程序](http://30ke.cn/code/js-array-method/some)

#### 3.7.3 every-函数完全检测

`Array.prototype.every()` 检测数组中是否所有元素都可以通过检测函数验证。

```js
var array1 = [ 1, 2, 3, 4, 5 ];
console.log(array1.every(x => x < 8));    //输出 true
console.log(array1.every(x => x < 4));    //输出 false

```

[查看示例程序](http://30ke.cn/code/js-array-method/every)

### 3.8 合并

#### 3.8.1 join-合并成字符串

`Array.prototype.join()` 合并数组中所有元素成为字符串并返回。

```js
var array1= [ 'a', 'b', 'c' ];
console.log(array1.join());    // 输出 a,b,c
console.log(array1.join("-"));   // 输出 a-b-c

```

[查看示例程序](http://30ke.cn/code/js-array-method/join)

#### 3.8.2 concat-合并成数组

`Array.prototype.concat()`  合并两个或多个数组，返回一个全新数组，原数组不变。

```js
var array1 = [ 'a', 'b' ];
var array2 = [ 'c', 'd' ];
console.log(array1.concat(array2));    // 输出 [ "a", "b", "c", "d" ]

```

该方法可以有多个参数。

[查看示例程序](http://30ke.cn/code/js-array-method/concat)

### 3.9 累计

#### 3.9.1 reduce-左侧累计

`Array.prototype.reduce()` 从左至右按 `reducer` 函数组合元素值，并返回累计器终值。

```js
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;
// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));    // 输出 10
// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));    // 输出 15，其中5是累计器初始值。

```

[查看示例程序](http://30ke.cn/code/js-array-method/reduce)

#### 3.9.2 reduceRight-右侧累计

`Array.prototype.reduceRight()` 从右至左按 `reducer` 函数组合元素值，并返回累计器终值。

```js
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator.concat(currentValue);
console.log(array1.reduceRight(reducer));    // 输出 [ 4, 3, 2, 1 ]
console.log(array1.reduceRight(reducer, 5));    // 输出 [ 5, 4, 3, 2, 1 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/reduceRight)

### 3.10 copyWithin-内部复制

`Array.prototype.copyWithin()`  数组内部复制，不改变原数组长度。

```
var array1 = ['a', 'b', 'c', 'd', 'e','f'];
console.log(array1.copyWithin(0, 3, 5));    // 输出 [ "d", "e", "c", "d", "e", "f" ]
console.log(array1.copyWithin(1, 3));    // 输出 [ "d", "d", "e", "f", "e", "f" ]

```

> ```js
> arr.copyWithin(target[, start[, end]])
> ```

- 参数`target` : 表示要复制到的索引位置，如为负值则从后向前计数。
- 参数`start` : 表示要复制序列的起始索引位置，如为负值则从后向前计数。如省略该值，则从索引0开始。
- 参数`end` : 表示要复制序列的结束位置，如为负值则从后向前计数。如省略该值，则复制到结尾位置。

[查看示例程序](http://30ke.cn/code/js-array-method/copyWithin)

### 3.11 fill-填充函数

`Array.prototype.fill()`  用固定值填充起始索引到终止索引区间内的全部元素值，不包括终止索引。

```js
var array1 = [1, 2, 3, 4];
console.log(array1.fill(9, 2, 4));    // 输出 [ 1, 2, 9, 9 ]
console.log(array1.fill(8, 1));      // 输出 [ 1, 8, 8, 8 ]
console.log(array1.fill(7));          // 输出 [ 7, 7, 7, 7 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/fill)

### 3.12 filter-过滤函数

`Array.prototype.filter()` 生成由通过检测函数验证元素组成的新数组并返回。

```js
var arr = [ 9 , 8 , 7 , 6];
console.log(arr.filter(x => x >7));    //输出 [ 9, 8 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/filter)

### 3.13 flat-数组扁平化

`Array.prototype.flat()`  按指定深度递归遍历数组，并返回包含所有遍历到的元素组成的新数组。不改变原数组。

```js
var arr1 = [ 1, 2, [ 3, 4 ] ];
console.log(arr1.flat());     // 输出 [ 1, 2, 3, 4 ]
var arr2 = [ 1, 2, [3, 4, [ 5, 6 ] ] ];
console.log(arr2.flat());    // 输出 [ 1, 2, 3, 4,  [ 5, 6 ] ]
var arr3 = [1, 2, [ 3, 4, [ 5, 6 ] ] ];
console.log(arr3.flat(2));    // 输出 [ 1, 2, 3, 4, 5, 6 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/flat)

### 3.14 map-映射

`Array.prototype.map()`  创建一个新数组，该数组中的元素由原数组元素调用map函数产生。

```js
var array1 = [1, 2, 3, 4];
console.log(array1.map(x => x * 2));    // 输出 [ 2, 4, 6, 8 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/map)

### 3.15 slice-截取数组

`Array.prototype.slice()` 按参数`begin` 和 `end` 截取数组，不改变原数组。

```js
var array1 = [ 1, 2, 3, 4, 5];
console.log(array1.slice( 2, 4 ));    //输出 [ 3, 4 ]
console.log(array1);    //输出 [ 1, 2, 3, 4, 5 ]

```

[查看示例程序](http://30ke.cn/code/js-array-method/slice)

## 4 结尾

### 4.1 结语

文中介绍的过于简单，想更多理解相关内容还是要多多动手实践！

因时间不足，能力有限等原因，存在文字阐述不准及代码测试不足等诸多问题。如发现错误请不吝指正！谢谢。



作者：毛瑞_三十课链接：https://juejin.im/post/5cc792666fb9a03239689682来源：掘金著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。