# Array有关的知识点

## 创建数组的几种方式？

1.使用`Array`构造函数，可以省略`new`操作符：
```javascript
let colors = new Array();
let colors1 = new Array(3); // 创建一个初始长度为3的数组
let colors2 = new Array('red', 'green', 'blue'); // 参数作为数组内要保存的元素
```
2.使用数组字面量直接表示，不会调用`Array`构造函数。

## `Array.from()`和`Array.of()`方法的区别？

**`Array.from()`**：可以把类数组对象转换为数组实例。
- 可以接受三个参数，第一个参数是待转换的类数组对象，该对象只要可迭代，或者有`length`属性和可索引的元素就行。
- 第二个参数是可选的，是一个函数，可以对数组每一项做处理再返回。
- 第三个可选的参数用于指定第二个参数的this值。
```javascript
const a1 = [1, 2, 3, 4];
const a2 = Array.from(a1, x => x ** 2);
const a3 = Array.from(a1, function(x) {
  return x ** this.exponent;
}, { exponent: 2});

console.log(a2); // [1, 4, 9, 16]
console.log(a3); // [1, 4, 9, 16]
```  

**`Array.of()`**：可以将一组参数转化为数组。
```javascript
console.log(Array.of(1, 2, 3, 4)); // [1, 2, 3, 4]
```

## 数组的`length`属性时只读的吗？
不是，修改`length`的值可以在数组末尾删除或添加元素。

## 如何判断一个对象是不是数组？
使用`Array.isArray()`方法。