---
title: Array.prototype.at()
slug: Web/JavaScript/Reference/Global_Objects/Array/at
---

{{JSRef}}

**`at()`** 方法接收一个整数值并返回该索引对应的元素，允许正数和负数。负整数从数组中的最后一个元素开始倒数。

{{EmbedInteractiveExample("pages/js/array-at.html")}}

## 语法

```js-nolint
at(index)
```

### 参数

- `index`
  - : 要返回的数组元素的索引（位置）。当传递负数时，支持从数组末端开始的相对索引；也就是说，如果使用负数，返回的元素将从数组的末端开始倒数。

### 返回值

匹配给定索引的数组中的元素。如果找不到指定的索引，则返回 {{jsxref('undefined')}}。

## 描述

在传递非负数时，`at()` 方法等价于括号表示法。例如，`array[0]` 和 `array.at(0)` 均返回第一个元素。但是，当你需要从数组的末端开始倒数时，则不能使用 Python 和 R 语言中支持的 `array[-1]`，因为方括号内的所有值都会被视为字符串属性，因此你最终读取的是 `array["-1"]`，这只是一个普通的字符串属性而不是数组索引。

通常的做法是访问 {{jsxref("Array/length", "length")}} 并将其减去从末端开始的相对索引。例如，`array[array.length - 1]`。`at()` 方法允许使用相对索引，因此上面的示例可以简化为 `array.at(-1)`。更正式地，当 `index < 0` 时，该方法将访问索引 `index + array.length`。

`at()` 方法是[通用的](/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#通用数组方法)。其仅期望 `this` 具有 `length` 属性和以整数为键的属性。

## 示例

### 返回数组的最后一个值

下面的示例提供了一个函数，它返回在一个指定的数组中找到的最后一个元素。

```js
// 数组及数组元素
const cart = ['apple', 'banana', 'pear'];

// 一个函数，用于返回给定数组的最后一个元素
function returnLast(arr) {
  return arr.at(-1);
}

// 获取 'cart' 数组的最后一个元素
const item1 = returnLast(cart);
console.log(item1); // 输出：'pear'

// 在 'cart' 数组中添加一个元素
cart.push('orange');
const item2 = returnLast(cart);
console.log(item2); // 输出：'orange'
```

### 比较不同的数组方法

这个示例比较了选择 {{jsxref('Array')}} 中倒数第二个元素的不同方法。虽然下面显示的所有方法都是可行的，但这个示例凸显了 `at()` 方法的简洁性和可读性。

```js
// 数组及数组元素
const colors = ['red', 'green', 'blue'];

// 使用长度属性
const lengthWay = colors[colors.length-2];
console.log(lengthWay); // 输出：'green'

// 使用 slice() 方法。注意会返回一个数组
const sliceWay = colors.slice(-2, -1);
console.log(sliceWay[0]); // 输出：'green'

// 使用 at() 方法
const atWay = colors.at(-2);
console.log(atWay); // 输出：'green'
```

### 在非数组对象上调用 at()

`at()` 方法读取 `this` 的 `length` 属性并计算需要访问的索引。

```js
const arrayLike = {
  length: 2,
  0: "a",
  1: "b",
};
console.log(Array.prototype.at.call(arrayLike, -1)); // "b"
```

## 规范

{{Specifications}}

## 浏览器兼容

{{Compat}}

## 参见

- [`core-js` 中 `Array.prototype.at` 的 polyfill](https://github.com/zloirock/core-js#relative-indexing-method)
- [at() 方法的一个 polyfill](https://github.com/tc39/proposal-relative-indexing-method#polyfill)。
- {{jsxref("Array.prototype.find()")}}——根据给定的测试返回一个值。
- {{jsxref("Array.prototype.includes()")}}——测试数组中是否存在某个值。
- {{jsxref("Array.prototype.indexOf()")}}——返回一个给定元素的索引。
- [索引集合类](/en-US/docs/Web/JavaScript/Guide/Indexed_collections)
