---
title: 索引集合类 (Indexed collections)
slug: Web/JavaScript/Guide/Indexed_collections
translation_of: Web/JavaScript/Guide/Indexed_collections
---
{{jsSidebar("JavaScript Guide")}} {{PreviousNext("Web/JavaScript/Guide/Regular_Expressions", "Web/JavaScript/Guide/Keyed_Collections")}}

这个章节主要介绍了以索引进行排序的数据集合。包括数组以及类似于数组的数据结构，如 **{{jsxref("Array")}}** 、**{{jsxref("TypedArray")}}** 。

## 数组对象 (Array object)

数组 (array) 是一个有序的数据集合，我们可以通过数组名称 (name) 和索引 (index) 进行访问。例如，我们定义了一个数组 emp，数组中的每个元素包含了一个雇员的名字以及其作为索引的员工号。那么 emp\[1] 将会代表 1 号员工，emp\[2] 将会代表 2 号员工，以此类推。

JavaScript 中没有明确的数组数据类型。但是，我们可以通过使用内置 Array 对象和它的方法对数组进行操作。Array 对象有很多操作数组的方法，比如合并、反转、排序等。数组对象有一个决定数组长度和使用正则表达式操作其他属性的属性。

### 创建数组 (creating an array)

以下语句创建等效的数组：

```js
var arr = new Array(element0, element1, ..., elementN);
var arr = Array(element0, element1, ..., elementN);
var arr = [element0, element1, ..., elementN];

// 译者注: var arr=[4] 和 var arr=new Array(4) 是不等效的，
// 后者 4 指数组长度，所以使用字面值 (literal) 的方式应该不仅仅是便捷，同时也不易踩坑
```

`element0, element1, ..., elementN` 是数组元素的值的列表。当这些值被指定后，数组将被初始化，他们将被作为数组元素。数组的 length 属性也会被设为参数的个数。

括号语法被称为 "数组字面值" 或 "数组初始化器", 它比其他创建数组的方式更便捷，所以通常是首选。详细内容参见 [Array literals](/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#Array_literals) 。

为了创建一个长度不为 0，但是又没有任何元素的数组，可选以下任何一种方式：

```js
var arr = new Array(arrayLength);
var arr = Array(arrayLength);

// 这样有同样的效果
var arr = [];
arr.length = arrayLength;
```

> **备注：**以上代码，数组长度（arrayLength）必须为一个数字（Number）。否则，将会创建一个只有单个（所输入的）元素的数组。 调用 `arr.length` 会返回数组长度，但是数组实际上包含了空的（`undefined`）元素。 因此在数组上使用 [`for...in`](/en-US/docs/Web/JavaScript/Reference/Statements/for...in) 循环，将不会返回任何的值 。

除了如上所示创建新定义的变量，数组 (array) 也可以作为一个属性 (property) 分配给一个新的或者已存在的对象 (object)：

```js
var obj = {};
// ...
obj.prop = [element0, element1, ..., elementN];

// OR
var obj = {prop: [element0, element1, ...., elementN]}
```

如果你希望用单个元素初始化一个数组，而这个元素恰好又是数字 (`Number`)，那么你必须使用括号语法。当单个的数字 (`Number`) 传递给 Array() 构造函数时，将会被解释为数组长度，并非单个元素。

```js
var arr = [42];      // 创建一个只有唯一元素的数组：
                     // the number 42.
var arr = Array(42); // 创建一个没有元素的数组，
                     // 但是数组的长度被设置成 42.

// 上面的代码与下面的代码等价
var arr = [];
arr.length = 42;
```

如果 N 不是一个整数，调用`Array(N)`将会报`RangeError`错误， 以下方法说明了这种行为：

```js
var arr = Array(9.3);  // RangeError: Invalid array length
```

如果你需要创建任意类型的单元素数组，安全的方式是使用字面值。或者在向数组添加单个元素之前先创建一个空的数组。

### 填充数组 (populating an array)

你可以通过给元素赋值来填充数组，例如：

```js
var emp = [];
emp[0] = "Casey Jones";
emp[1] = "Phil Lesh";
emp[2] = "August West";
```

> **备注：**如果你在以上代码中给数组操作符的是一个非整形数值，那么将作为一个代表数组的对象的属性 (property) 创建，而非作为数组的元素。

```js
var arr = [];
arr[3.4] = "Oranges";
console.log(arr.length);                // 0
console.log(arr.hasOwnProperty(3.4));   // true
```

你也可以在创建数组的时候去填充它：

```js
var myArray = new Array("Hello", myVar, 3.14159);
var myArray = ["Mango", "Apple", "Orange"]
```

### 引用数组元素 (referring to array elements)

您通过可以使用元素的序号来引用数组的元素。例如，假设你定义了如下数组：

```js
var myArray = ["Wind", "Rain", "Fire"];
```

你可以用 `myArray[0]`引用第一个元素，`myArray[1]`引用第二个元素。元素的索引是从`0`开始的。

> **备注：**数组操作符（方括号 \[ ]）也可以用来访问数组的属性 (在 JavaScript 中，数组也是对象)。例如：

```js
var arr = ["one", "two", "three"];
arr[2];  // three
arr["length"];  // 3
```

### 理解 length

在实施层面， JavaScript 实际上是将元素作为标准的对象属性来存储，把数组索引作为属性名。长度属性是特殊的，它总是返回最后一个元素的索引值加 1(下例中， Dusty 的索引是 30，所以 cats.length 返回 30 + 1)。记住， JavaScript 数组索引是基于 0 的：他们从 0 开始，而不是 1。这意味着数组长度属性将比最大的索引值大 1:

```js
var cats = [];
cats[30] = ['Dusty'];
console.log(cats.length); // 31
```

你也可以分配`length`属性。写一个小于数组元素数量的值会缩短数组，写 0 会彻底清空数组：

```js
var cats = ['Dusty', 'Misty', 'Twiggy'];
console.log(cats.length); // 3

cats.length = 2;
console.log(cats); // logs "Dusty,Misty" - Twiggy has been removed

cats.length = 0;
console.log(cats); // logs nothing; the cats array is empty

cats.length = 3;
console.log(cats); // [undefined, undefined, undefined]
```

### 遍历数组 (interating over array)

遍历数组元素并以某种方式处理每个元素是一个常见的操作。以下是最简单的方式：

```js
var colors = ['red', 'green', 'blue'];
for (var i = 0; i < colors.length; i++) {
  console.log(colors[i]);
}
```

如果你确定数组中没有一个元素的求值是 false —— 如果你的数组只包含[DOM](/en-US/docs/DOM)节点，如下，你可以选择一个更高效的土法子：

```js
var divs = document.getElementsByTagName('div');
for (var i = 0, div; div = divs[i]; i++) {
  /* Process div in some way */
}
```

这样避免了检测数组长度的开销，额外的好处是确保了 div 变量当前在每次循环中都被重新赋值为当前项。

{{jsxref("Array.forEach", "forEach()")}} 方法提供了遍历数组元素的其他方法：

```js
var colors = ['red', 'green', 'blue'];
colors.forEach(function(color) {
  console.log(color);
});
```

被传递给 forEach 的函数会在数组的每个元素像上执行一次，元素作为参数传递给该函数。未赋值的值不会在 forEach 循环迭代。

注意，在数组定义时省略的元素不会在 forEach 遍历时被列出，但是手动赋值为 undefined 的元素是会被列出的：

```js
var array = ['first', 'second', , 'fourth'];

// returns ['first', 'second', 'fourth'];
array.forEach(function(element) {
  console.log(element);
})

if(array[2] === undefined) { console.log('array[2] is undefined'); } // true

var array = ['first', 'second', undefined, 'fourth'];

// returns ['first', 'second', undefined, 'fourth'];
array.forEach(function(element) {
  console.log(element);
})
```

一旦 JavaScript 元素被保存为标准的对象属性，通过[`for...in`](/en-US/docs/Web/JavaScript/Reference/Statements/for...in) 循环来迭代数组将变得不明智，因为正常元素和所有可枚举的属性都会被列出。

### 数组的方法 (array methods)

{{jsxref("Array")}} 对象具有下列方法：

{{jsxref("Array.concat", "concat()")}} 连接两个数组并返回一个新的数组。

```js
var myArray = new Array("1", "2", "3");
myArray = myArray.concat("a", "b", "c");
// myArray is now ["1", "2", "3", "a", "b", "c"]
```

{{jsxref("Array.join", "join(deliminator = ',')")}} 将数组的所有元素连接成一个字符串。

```js
var myArray = new Array("Wind", "Rain", "Fire");
var list = myArray.join(" - "); // list is "Wind - Rain - Fire"
```

{{jsxref("Array.push", "push()")}} 在数组末尾添加一个或多个元素，并返回数组操作后的长度。

```js
var myArray = new Array("1", "2");
myArray.push("3"); // myArray is now ["1", "2", "3"]
```

{{jsxref("Array.pop", "pop()")}} 从数组移出最后一个元素，并返回该元素。

```js
var myArray = new Array("1", "2", "3");
var last = myArray.pop();
// myArray is now ["1", "2"], last = "3"
```

{{jsxref("Array.shift", "shift()")}} 从数组移出第一个元素，并返回该元素。

```js
var myArray = new Array ("1", "2", "3");
var first = myArray.shift();
// myArray is now ["2", "3"], first is "1"
```

{{jsxref("Array.shift", "unshift()")}} 在数组开头添加一个或多个元素，并返回数组的新长度。

```js
var myArray = new Array ("1", "2", "3");
myArray.unshift("4", "5");
// myArray becomes ["4", "5", "1", "2", "3"]
```

{{jsxref("Array.slice", "slice(start_index, upto_index)")}} 从数组提取一个片段，并作为一个新数组返回。

```js
var myArray = new Array ("a", "b", "c", "d", "e");
myArray = myArray.slice(1, 4); // 包含索引 1，不包括索引 4
                               // returning [ "b", "c", "d"]
```

{{jsxref("Array.splice", "splice(index, count_to_remove, addElement1, addElement2, ...)")}}从数组移出一些元素，（可选）并替换它们。

```js
var myArray = new Array ("1", "2", "3", "4", "5");
myArray.splice(1, 3, "a", "b", "c", "d");
// myArray is now ["1", "a", "b", "c", "d", "5"]
// This code started at index one (or where the "2" was),
// removed 3 elements there, and then inserted all consecutive
// elements in its place.
```

{{jsxref("Array.reverse", "reverse()")}} 颠倒数组元素的顺序：第一个变成最后一个，最后一个变成第一个。

```js
var myArray = new Array ("1", "2", "3");
myArray.reverse();
// transposes the array so that myArray = [ "3", "2", "1" ]
```

{{jsxref("Array.sort", "sort()")}} 给数组元素排序。

```js
var myArray = new Array("Wind", "Rain", "Fire");
myArray.sort();
// sorts the array so that myArray = [ "Fire", "Rain", "Wind" ]
```

`sort()` 也可以带一个回调函数来决定怎么比较数组元素。这个回调函数比较两个值，并返回 3 个值中的一个：

例如，下面的代码通过字符串的最后一个字母进行排序：

```js
var sortFn = function(a, b){
  if (a[a.length - 1] < b[b.length - 1]) return -1;
  if (a[a.length - 1] > b[b.length - 1]) return 1;
  if (a[a.length - 1] == b[b.length - 1]) return 0;
}
myArray.sort(sortFn);
// sorts the array so that myArray = ["Wind","Fire","Rain"]
```

- 如果 a 小于 b ，返回 -1(或任何负数)
- 如果 `a` 大于 `b` ，返回 1 (或任何正数)
- 如果 `a` 和 `b` 相等，返回 0。

{{jsxref("Array.indexOf", "indexOf(searchElement[, fromIndex])")}} 在数组中搜索`searchElement` 并返回第一个匹配的索引。

```js
var a = ['a', 'b', 'a', 'b', 'a'];
console.log(a.indexOf('b')); // logs 1
// Now try again, starting from after the last match
console.log(a.indexOf('b', 2)); // logs 3
console.log(a.indexOf('z')); // logs -1, because 'z' was not found
```

{{jsxref("Array.lastIndexOf", "lastIndexOf(searchElement[, fromIndex])")}} 和 `indexOf 差不多，但这是从结尾开始，并且是反向搜索。`

```js
var a = ['a', 'b', 'c', 'd', 'a', 'b'];
console.log(a.lastIndexOf('b')); // logs 5
// Now try again, starting from before the last match
console.log(a.lastIndexOf('b', 4)); // logs 1
console.log(a.lastIndexOf('z')); // logs -1
```

{{jsxref("Array.forEach", "forEach(callback[, thisObject])")}} 在数组每个元素项上执行`callback`。

```js
var a = ['a', 'b', 'c'];
a.forEach(function(element) { console.log(element);} );
// logs each item in turn
```

{{jsxref("Array.map", "map(callback[, thisObject])")}} 在数组的每个单元项上执行 callback 函数，并把返回包含回调函数返回值的新数组（译者注：也就是遍历数组，并通过 callback 对数组元素进行操作，并将所有操作结果放入数组中并返回该数组）。

```js
var a1 = ['a', 'b', 'c'];
var a2 = a1.map(function(item) { return item.toUpperCase(); });
console.log(a2); // logs A,B,C
```

{{jsxref("Array.filter", "filter(callback[, thisObject])")}} 返回一个包含所有在回调函数上返回为 true 的元素的新数组（译者注：callback 在这里担任的是过滤器的角色，当元素符合条件，过滤器就返回 true，而 filter 则会返回所有符合过滤条件的元素）。

```js
var a1 = ['a', 10, 'b', 20, 'c', 30];
var a2 = a1.filter(function(item) { return typeof item == 'number'; });
console.log(a2); // logs 10,20,30
```

{{jsxref("Array.every", "every(callback[, thisObject])")}} 当数组中每一个元素在 callback 上被返回 true 时就返回 true（译者注：同上，every 其实类似 filter，只不过它的功能是判断是不是数组中的所有元素都符合条件，并且返回的是布尔值）。

```js
function isNumber(value){
  return typeof value == 'number';
}
var a1 = [1, 2, 3];
console.log(a1.every(isNumber)); // logs true
var a2 = [1, '2', 3];
console.log(a2.every(isNumber)); // logs false
```

{{jsxref("Array.some", "some(callback[, thisObject])")}} 只要数组中有一项在 callback 上被返回 true，就返回 true（译者注：同上，类似 every，不过前者要求都符合筛选条件才返回 true，后者只要有符合条件的就返回 true）。

```js
function isNumber(value){
  return typeof value == 'number';
}
var a1 = [1, 2, 3];
console.log(a1.some(isNumber)); // logs true
var a2 = [1, '2', 3];
console.log(a2.some(isNumber)); // logs true
var a3 = ['1', '2', '3'];
console.log(a3.some(isNumber)); // logs false
```

以上方法都带一个被称为迭代方法的的回调函数，因为他们以某种方式迭代整个数组。都有一个可选的第二参数 `thisObject`，如果提供了这个参数，`thisObject` 变成回调函数内部的 this 关键字的值。如果没有提供，例如函数在一个显示的对象上下文外被调用时，this 将引用全局对象 ({{domxref("window")}}).

实际上在调用回调函数时传入了 3 个参数。第一个是当前元素项的值，第二个是它在数组中的索引，第三个是数组本身的一个引用。 JavaScript 函数忽略任何没有在参数列表中命名的参数，因此提供一个只有一个参数的回调函数是安全的，例如 `alert` 。

{{jsxref("Array.reduce", "reduce(callback[, initialValue])")}} 使用回调函数 `callback(firstValue, secondValue)` 把数组列表计算成一个单一值（译者注：他数组元素两两递归处理的方式把数组计算成一个值）

```js
var a = [10, 20, 30];
var total = a.reduce(function(first, second) { return first + second; }, 0);
console.log(total) // Prints 60
```

{{jsxref("Array.reduceRight", "reduceRight(callback[, initalvalue])")}} 和 `reduce() 相似，但这从最后一个元素开始的。`

`reduce` 和 `reduceRight` 是迭代数组方法中最不被人熟知的两个函数.。他们应该使用在那些需要把数组的元素两两递归处理，并最终计算成一个单一结果的算法。

### 多维数组 (multi-dimensional arrays)

数组是可以嵌套的，这就意味着一个数组可以作为一个元素被包含在另外一个数组里面。利用 JavaScript 数组的这个特性，可以创建多维数组。

以下代码创建了一个二维数组。

```js
var a = new Array(4);
for (i = 0; i < 4; i++) {
  a[i] = new Array(4);
  for (j = 0; j < 4; j++) {
    a[i][j] = "[" + i + "," + j + "]";
  }
}
```

这个例子创建的数组拥有以下行数据：

```plain
Row 0: [0,0] [0,1] [0,2] [0,3]
Row 1: [1,0] [1,1] [1,2] [1,3]
Row 2: [2,0] [2,1] [2,2] [2,3]
Row 3: [3,0] [3,1] [3,2] [3,3]
```

### 数组和正则表达式

当一个数组作为字符串和正则表达式的匹配结果时，该数组将会返回相关匹配信息的属性和元素。 [`RegExp.exec()`](/en-US/docs/JavaScript/Reference/Global_Objects/RegExp/exec), `String.match() 和` `String.split() 的返回值是一个数组。` 使用数组和正则表达式的的更多信息，请看 [Regular Expressions](/en-US/docs/Web/JavaScript/Guide/Regular_Expressions).

### 使用类数组对象 (array-like objects)

一些 JavaScript 对象，例如 {{domxref("document.getElementsByTagName()")}} 返回的 {{domxref("NodeList")}} 或者函数内部可用的 [`arguments`](/en-US/docs/Web/JavaScript/Reference/Functions/arguments) 对象，他们表面上看起来，外观和行为像数组，但是不共享他们所有的方法。例如 `arguments` 对象就提供一个 [`length`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/length) 属性，但是不实现 {{jsxref("Array.forEach", "forEach()")}} 方法。

Array 的原生 (prototype) 方法可以用来处理类似数组行为的对象，例如： :

```js
function printArguments() {
  Array.prototype.forEach.call(arguments, function(item) {
    console.log(item);
  });
}
```

Array 的常规方法也可以用于处理字符串，因为它提供了序列访问字符转为数组的简单方法：

```js
Array.prototype.forEach.call("a string", function(chr) {
  console.log(chr);
});
```

## 数组推导式（Array comprehensions）

在[JavaScript 1.7](/en-US/docs/Web/JavaScript/New_in_JavaScript/1.7) 被介绍并计划在 [ECMAScript 7](/en-US/docs/Web/JavaScript/New_in_JavaScript/ECMAScript_7_support_in_Mozilla), [array comprehensions](/en-US/docs/Web/JavaScript/Reference/Operators/Array_comprehensions) 被规范化并提供一个有用的快捷方式，用来实现如何在另一个数组的基础上构造一个新的数组。推导式可以经常被用在那些需要调用 `map()` 和 `filter() 函数的地方，`或作为一种结合这两种方式。

下面的推导式创建一个数字数组并且创建一个新的数组，数组的每个元素都是原来数值的两倍（译者注：这种形式类似于 Python 的列表推导式）。

```js
var numbers = [1, 2, 3, 4];
var doubled = [for (i of numbers) i * 2];
console.log(doubled); // logs 2,4,6,8
```

这跟下面的 map() 方法的操作是等价的。

```js
var doubled = numbers.map(function(i){return i * 2;});
```

推导式也可以用来筛选满足条件表达式的元素。下面的推导式用来筛选是 2 的倍数的元素：

```js
var numbers = [1, 2, 3, 21, 22, 30];
var evens = [i for (i of numbers) if (i % 2 === 0)];
console.log(evens); // logs 2,22,30
```

`filter()` 也可以达到相同的目的：

```js
var evens = numbers.filter(function(i){return i % 2 === 0;});
```

`map()` `和 filter()` 类型的操作可以被组合（等效）为单个数组推导式。这里就有一个过滤出偶数，创建一个它的倍数数组的例子：

```js
var numbers = [1, 2, 3, 21, 22, 30];
var doubledEvens = [i * 2 for (i of numbers) if (i % 2 === 0)];
console.log(doubledEvens); // logs 4,44,60
```

数组推导式隐含了块作用域。新的变量 (如例子中的 i) 类似于是采用 [`let`](/en-US/docs/Web/JavaScript/Reference/Statements/let)声明的。这意味着他们不能在推导式以外访问。

数组推导式的输入不一定必须是数组; [迭代器和生成器](/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) 也是可以的。

甚至字符串也可以用来作为输入; 实现 filter 或者 map 行为 (参考上面类似数组行为的对象) 如下：

```js
var str = 'abcdef';
var consonantsOnlyStr = [c for (c of str) if (!(/[aeiouAEIOU]/).test(c))  ].join(''); // 'bcdf'
var interpolatedZeros = [c+'0' for (c of str) ].join(''); // 'a0b0c0d0e0f0'
```

不过，输入形式是不能保存的，所以我们要使用 join() 回复到一个字符串。

## 类型化数组 (Typed Arrays )

[JavaScript typed arrays](/en-US/docs/Web/JavaScript/Typed_arrays) 是类数组对象（array-like object），其提供访问原始二进制数据的机制。 就像你知道的那样，{{jsxref("Array")}} 对象动态增长和收缩，可以有任何 JavaScript 值。但对于类型化数组，JavaScript 引擎执行优化使得这些数组访问速度快速。 随着 Web 应用程序变得越来越强大，添加音频和视频处理等功能、可以使用 [WebSockets](/en-US/docs/WebSockets) 、使用原始数据， 这都需要访问原始的二进制数据，所以专门的优化将有助于 JavaScript 代码能够快速和容易地操纵原始二进制数据类型的数组。

### 缓冲区和视图：类型化的数组结构

为了实现最大的灵活性和效率，JavaScript 类型数组被分解为缓冲 (Buffer) 和视图 (views)。缓冲 (由{{jsxref("ArrayBuffer")}} 实现) 是代表数据块的对象，它没有格式可言，并没有提供任何机制来访问其内容。为了访问包含在缓冲区中的内存，您需要使用视图。视图提供了一个上下文，即数据类型、起始偏移量和元素数，这些元素将数据转换为实际类型数组。

![Typed arrays in an ArrayBuffer](typed_arrays.png)

### ArrayBuffer

{{jsxref("ArrayBuffer")}}是一种数据类型，用于表示一个通用的、固定长度的二进制数据缓冲区。你不能直接操纵一个 ArrayBuffer 中的内容；你需要创建一个数组类型视图或{{jsxref("DataView")}}来代表特定格式的缓冲区，并从而实现读写缓冲区的内容。

### 类型数组视图 (Typed array views)

类型数组视图具有自描述性的名字，并且提供数据类型信息，例如`Int8`, `Uint32`, `Float64 等等。`如一个特定类型数组视图`Uint8ClampedArray`. 它意味着数据元素只包含 0 到 255 的整数值。它通常用于[Canvas 数据处理](/en-US/docs/Web/API/ImageData),例如。

{{page("/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray", "TypedArray_objects")}}

更多信息参考 [JavaScript typed arrays](/en-US/docs/Web/JavaScript/Typed_arrays) 与参考文档中 {{jsxref("TypedArray")}}对象的不同

{{PreviousNext("Web/JavaScript/Guide/Regular_Expressions", "Web/JavaScript/Guide/Keyed_Collections")}}
