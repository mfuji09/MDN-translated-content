---
title: Array.prototype.reverse()
slug: Web/JavaScript/Reference/Global_Objects/Array/reverse
tags:
  - Array
  - JavaScript
  - Method
  - Prototype
translation_of: Web/JavaScript/Reference/Global_Objects/Array/reverse
---
{{JSRef}}

**`reverse()`** 方法會*[原地（in place）](https://zh.wikipedia.org/wiki/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)*反轉（reverses）一個陣列。陣列中的第一個元素變為最後一個，而最後一個元素則變成第一個。

{{EmbedInteractiveExample("pages/js/array-reverse.html")}}

## 語法

```plain
a.reverse()
```

### 回傳值

反轉後的陣列。

## 描述

`reverse` 方法將原地（in place）變換（transposes）呼叫此方法的陣列物件之元素至其顛倒的位置，改變原陣列後，並回傳此陣列之參考位址（reference）。

## 範例

### 反轉陣列中之元素

下列範例建立了一個包含三個元素的陣列 `a`，接著反轉此陣列。呼叫 `reverse()` 會回傳一個反轉後的原陣列 `a` 之參考。

```js
var a = ['one', 'two', 'three'];
var reversed = a.reverse();

console.log(a);        // ['three', 'two', 'one']
console.log(reversed); // ['three', 'two', 'one']
```

## 規範

{{Specifications}}

## 瀏覽器相容性

{{Compat("javascript.builtins.Array.reverse")}}

## 參見

- {{jsxref("Array.prototype.join()")}}
- {{jsxref("Array.prototype.sort()")}}
- {{jsxref("TypedArray.prototype.reverse()")}}
