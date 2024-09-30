# <center>javascript</center>

## <font class="text-color-13" color="#ffeb3b">概述</font>
* JavaScript 是一种动态、解释型的编程语言，最初由 Netscape 公司开发，用于在网页上实现交互式的效果。现在已成为 Web 前端开发中的重要一环，也被广泛应用于后端开发、桌面应用开发等领域。

* JavaScript 是一种弱类型语言，即不需要在定义变量时指定数据类型。它还支持面向对象编程、函数式编程等多种编程范式。JavaScript 的语法结构主要受到 C 和 Java 等语言的影响，同时还具有一些独特的特性，如闭包、原型继承、函数作为一等公民等。JavaScript 是一种解释型语言，它不需要像编译型语言那样进行编译。当 JavaScript 代码在浏览器中被执行时，它会被直接解释并执行。这就意味着，JavaScript 代码可以在浏览器中动态地修改和执行。

* JavaScript 通常与 HTML 和 CSS 一起使用，用于实现网页的交互效果。通过 JavaScript，可以实现网页元素的动态修改、响应用户的输入、处理表单数据、向服务器发送请求等功能。此外，JavaScript 还可以使用各种库和框架，如 jQuery、React、Vue 等，简化网页开发的过程。

* 除了在前端开发中的应用，JavaScript 还可以通过 Node.js 在服务器端运行，实现 Web 应用程序的后端逻辑。Node.js 提供了许多用于网络通信、文件操作等的 API，使得 JavaScript 可以在服务器端编写高效的程序。

* <a href="https://devdocs.io/javascript/">java script 文档</a>

### <font class="text-color-141" color="#ff9800">javascript 编程三大块</font>
1. DOM（文档对象模型）：用于处理HTML和XML文档的API（应用程序接口），它允许JavaScript代码通过修改文档的结构和内容来动态地更新页面。使用DOM，开发者可以选择、添加、删除或修改页面中的任何元素，以及监听和响应用户的交互事件。
  
2. BOM（浏览器对象模型）：用于处理浏览器窗口和标签页的API，它提供了访问和控制浏览器各种属性和方法的接口，如窗口大小、地址栏、历史记录、定时器等。BOM也提供了一些特定的对象，如navigator、location和screen等，可以用来获取浏览器的相关信息。
  
3. ES（ECMAScript）：是JavaScript语言的核心，定义了JavaScript的基础语法、数据类型、变量、函数、运算符等。ES标准由ECMA国际组织维护，JavaScript实现了ES标准，并在此基础上增加了一些扩展，使得JavaScript可以更方便地操作DOM和BOM等浏览器特有的功能。

## <font class="text-color-121" color="#ffeb3b">语法注意事项</font>
* JS 的字符串可以使用双引号，也可以使用单引号

* JS 的一条语句结束之后可以使用“ ; ” 也可以不用。

### <font class="text-color-141" color="#ff9800">let 和 var 区别</font>
#### <font class="text-color-61" color="#03a9f4">作用域不同</font>
	`var` 声明的变量是函数作用域或全局作用域，而 `let` 声明的变量是块级作用域。块级作用域指的是在 `{}` 内声明的变量只在该代码块内有效，代码块可以是函数、循环、条件语句等。
```javascript
function example1() {
  var x = 1;
  if (true) {
    var x = 2;
  }
  console.log(x); // 输出 2
}

function example2() {
  let x = 1;
  if (true) {
    let x = 2;
  }
  console.log(x); // 输出 1
}

example1();
example2();
```
#### <font class="text-color-61" color="#03a9f4">变量提升不同</font>
	使用 `var` 声明的变量存在变量提升，即在函数作用域内，无论变量声明在哪里，都会被提升到函数作用域的顶部，可以在声明之前访问变量。而使用 `let` 声明的变量不存在变量提升，只有在变量声明之后才能访问变量。
```javascript
function example3() {
  console.log(x); // 输出 undefined
  var x = 1;
}

function example4() {
  console.log(x); // 报错：x is not defined
  let x = 1;
}

example3();
example4();
```
#### <font class="text-color-61" color="#03a9f4">同名变量不同</font>
	使用 `var` 声明的变量在同一作用域内可以被重复声明，后面的声明会覆盖前面的声明。而使用 `let` 声明的变量在同一作用域内不允许重复声明，否则会抛出语法错误。
```javascript
function example5() {
  var x = 1;
  var x = 2;
  console.log(x); // 输出 2
}

function example6() {
  let x = 1;
  let x = 2; // 报错：Identifier 'x' has already been declared
  console.log(x);
}

example5();
example6();
```
* `let` 声明的变量相对于 `var` 更加严格，避免了变量提升和重复声明的问题，同时引入了块级作用域，使代码更加清晰和安全。在 ES6 之前，JavaScript 中没有块级作用域，这也是 `let` 语句出现的一个重要原因。
---
### <font class="text-color-15" color="#ff9800">作用域</font>
#### <font class="text-color-7" color="#03a9f4">全局变量</font>
* 在函数外部声明的变量是全局变量，可以在任何地方访问。全局变量通常被用来存储需要在整个程序中使用的数据。
```javascript
let globalVariable = 10;

function foo() {
  console.log(globalVariable); // 10
}

foo();
```
#### <font class="text-color-7" color="#03a9f4">局部变量</font>
* 在函数内部声明的变量是局部变量，只能在该函数内部访问。局部变量通常被用来存储需要在函数内部使用的数据。
```javascript
function foo() {
  let localVariable = 20;
  console.log(localVariable); // 20
}

foo();
console.log(localVariable); // ReferenceError: localVariable is not defined
```
#### <font class="text-color-7" color="#03a9f4">块级变量</font>
* 在块级作用域内声明的变量是块级变量，只能在该块级作用域内访问。块级变量通常被用来存储需要在一个块级作用域内使用的数据。
```javascript
{
  let blockVariable = 30;
  console.log(blockVariable); // 30
}

console.log(blockVariable); // ReferenceError: blockVariable is not defined
```
#### <font class="text-color-7" color="#03a9f4">隐式全局变量</font>
* 在 JavaScript 中，如果在申明变量时不加关键字 `var`、`let` 或 `const`，会默认将该变量声明为全局变量，即该变量的作用域是全局作用域。这种方式被称为“隐式全局变量”。

* 隐式全局变量的问题在于，它们容易与其他全局变量冲突，并且可能会导致命名冲突和不可预期的行为。此外，由于全局变量的生命周期很长，容易造成内存泄漏和安全问题。
```javascript
function foo() {
  bar = 'hello'; // 隐式声明全局变量 bar
}

foo();

console.log(bar); // 'hello'
```
### <font class="text-color-15" color="#ff9800">尾递归优化</font>
* ES6（ECMAScript 2015）引入了尾递归优化（Tail Call Optimization），这是一种优化尾递归函数的编译器优化技术，能够避免由于递归调用导致的堆栈溢出。

* 尾递归是指在函数的最后一步调用自身的递归，这样的递归称为尾递归。尾递归优化的核心是将递归调用的结果作为参数传递给下一次调用，这样就不需要创建新的堆栈帧，而是可以重用当前的帧，避免了栈溢出的问题。

```javascript
// 无尾递归
let fac1 = function (num){
    if(num === 0 || num === 1) return 1
    else return num * fac1(num -1)
}

// 累加器实现尾递归
let fac2 = function (num){
    let fac_tr = function (num,acc){
        if(num === 0 || num === 1) return acc
        else return fac_tr(num - 1,acc * num)
    }
    return  fac_tr(num,1)
}

// CPS实现尾递归
let fac3 = function (num){
    let fac_cps = function (fun,num){
        if(num === 0 || num === 1) return fun()
        else {
            return fac_cps(function () {
                return fun() * num
            },num - 1)
        }
    }
    return fac_cps(function () {
        return 1
    },num)
}

console.log(fac1(5)) // 120
console.log(fac2(5)) // 120
console.log(fac3(5)) // 120
```
* 这段代码展示了三种不同的阶乘函数实现方式：无尾递归、累加器实现尾递归、以及 CPS（Continuation Passing Style）实现尾递归。

* 第一个函数 `fac1` 是最简单的阶乘函数实现，但是由于是无尾递归，当传入的数值很大时，会引起栈溢出。

* 第二个函数 `fac2` 是使用累加器实现尾递归，避免了栈溢出问题。在每次递归调用时，都将计算结果累积到一个变量 `acc` 中，避免了函数调用栈不断增加导致的问题。这是一种常见的尾递归优化方式。

* 第三个函数 `fac3` 使用了 CPS 实现尾递归。CPS 是一种函数编程的技术，其中每个函数都接收一个额外的参数，这个参数是一个函数，称为 continuation，代表了程序继续执行的下一步。通过将计算结果作为参数传递给 continuation 函数，避免了函数调用栈不断增加导致的问题。这也是一种常见的尾递归优化方式。

* 在本例中，三个函数实现的结果都是相同的，都是计算 5 的阶乘，结果为 120。但是当传入的参数很大时，无尾递归的函数 `fac1` 会引起栈溢出问题，而使用尾递归的函数 `fac2` 和 `fac3` 则不会。

* 注：在实际使用中，一些JavaScript引擎，如V8和SpiderMonkey，可以对尾递归进行优化，但是并不是所有引擎都支持该优化。在ECMAScript 6标准中，对于需要进行优化的尾递归函数，应该满足一定的条件，如只在尾部调用自身、没有外部状态等，以帮助引擎实现尾调用优化。但是，即使函数符合这些条件，也不能保证JavaScript引擎一定会对其进行优化。在实践中，建议使用循环或其他方式来代替尾递归，以免出现栈溢出等问题。


 ## <font class="text-color-121" color="#ffeb3b">变量</font>
 * JavaScript 是一种弱类型（Weakly Typed）语言，也被称为动态类型（Dynamic Typed）语言。弱类型语言与强类型（Strongly Typed）语言相对，指的是在编程过程中对数据类型的定义和限制程度不同。

* 在弱类型语言中，变量的数据类型不需要在声明时显式指定，而是在程序运行过程中根据赋值语句自动推断，也可以在运行时动态修改变量类型。例如，以下代码中的 `a` 变量在赋值为字符串之后，就变成了字符串类型，而在赋值为数字时又变成了数字类型：
```javascript
let a = 'Hello'; // a 是字符串类型
a = 123; // a 是数字类型
```
* 弱类型语言的优点是编写代码更加灵活和方便，可以更快速地进行开发和测试。但是，它也带来了一些问题，如类型转换不当可能会导致程序出错，而且在开发大型复杂的项目时，可能需要更多的测试和调试工作来保证程序的正确性和稳定性。
---
### <font class="text-color-141" color="#ff9800">原始类型</font>

| 数据类型 | 描述 |
| --- | --- |
| Number | 表示数字，包括整数和浮点数。例如： 3, 3.14, NaN(非数字)。|
| String | 表示文本字符串，可以使用单引号、双引号或反引号来表示。例如："hello", 'world', \`hello \${name}\`。|
| Boolean | 表示逻辑值，只有两个值：true 和 false。|
| Null | 表示空值。该类型只有一个取值 null。|
| Undefined | 表示未定义的值。该类型只有一个取值 undefined。|
| Symbol | 表示唯一的标识符。ES6 中新增的数据类型，用于创建对象的属性名。例如：const key = Symbol('key')。|

```javascript
const numberExample = 123;
const stringExample = 'hello world';
const booleanExample = true;
const nullExample = null;
let undefinedExample;
const symbolExample = Symbol('symbol');

console.log(typeof numberExample); // 输出：number
console.log(typeof stringExample); // 输出：string
console.log(typeof booleanExample); // 输出：boolean
console.log(typeof nullExample); // 输出：object
console.log(typeof undefinedExample); // 输出：undefined
console.log(typeof symbolExample); // 输出：symbol
```
#### <font class="text-color-61" color="#03a9f4">NaN</font>
* 在JavaScript中，当数值类型的值无法表示为有效数字时，会返回一个特殊的值NaN（Not a Number）。NaN是一个特殊的数字，它表示不是一个数字，通常是由于错误的计算或数据类型转换错误导致的。一些常见的情况会导致NaN的产生，例如：
	1. 除以0得到的结果
	2. 对象转换成数值类型时出现错误
	3. 字符串解析成数值类型时出现错误
	4. 无法计算的数学运算，如0/0、Infinity - Infinity等等。

* 需要注意的是，NaN与任何值都不相等，包括NaN本身，因此不能使用常规的相等比较操作符（如==）来检查NaN是否相等。可以使用特殊的函数 `isNaN()` 来判断一个值是否为NaN。

#### <font class="text-color-61" color="#03a9f4">Infinity</font>
* 在JavaScript中，当数字被除以0或被赋予超过了最大数字的值时，就会出现Infinity。Infinity表示无穷大，它是一个特殊的数值类型，可以通过 `Number.POSITIVE_INFINITY` 或者 `1/0` 表示。当一个数字被除以0时，它的结果是无穷大，而当一个负数被除以0时，结果是负无穷大，可以通过 `Number.NEGATIVE_INFINITY` 或者 `-1/0` 表示。
---
### <font class="text-color-141" color="#ff9800">引用类型</font>

| 对象类型 | 描述 | 示例 |
| --- | --- | --- |
| Object | 对象是 JavaScript 的基本数据类型之一，可以看作是键值对的集合，每个键名对应一个值。 | {name: '张三', age: 20} |
| Array | 数组是一种特殊的对象，可以保存多个值，每个值都有一个索引，从 0 开始。 | [1, 2, 3] |
| Date | Date 对象表示时间和日期。 | new Date() |
| RegExp | RegExp 对象表示正则表达式。 | /\w+/g |
| Function | Function 对象是 JavaScript 中的函数类型。 | function sayHello() { console.log('Hello'); } |
| Error | Error 对象表示程序运行时发生的错误。 | new Error('出错了') |
| Math | Math 对象是一个数学工具对象，提供了许多数学计算的方法和常数。 | Math.PI |
| JSON | JSON 对象提供了 JSON 数据的解析和序列化功能。 | JSON.parse() 和 JSON.stringify() |

```javascript
const objectExample = { name: '张三', age: 20 };
const arrayExample = [1, 2, 3];
const dateExample = new Date();
const regExpExample = /\w+/g;
const functionExample = function sayHello() { console.log('Hello'); };
const errorExample = new Error('出错了');
const pi = Math.PI;
const jsonString = '{"name": "张三", "age": 20}';
const jsonObject = JSON.parse(jsonString);

console.log(typeof objectExample); // 输出：object
console.log(typeof arrayExample); // 输出：object
console.log(typeof dateExample); // 输出：object
console.log(typeof regExpExample); // 输出：object
console.log(typeof functionExample); // 输出：function
console.log(typeof errorExample); // 输出：object
console.log(typeof pi); // 输出：number
console.log(typeof jsonObject); // 输出：object

```
### <font class="text-color-141" color="#ff9800">typeof</font>
* 在 JavaScript 中，`typeof` 是一个操作符，用于确定变量或表达式的数据类型。`typeof` 返回一个字符串，表示给定值的数据类型。

* `typeof` 的用法：
```javascript
typeof variable;
typeof expression;
// 其中，`variable` 是一个变量名，`expression` 是一个表达式，例如 `5`，`"hello"` 等。
```
* `typeof` 可以返回以下数据类型的字符串表示：

	- `"undefined"`：表示变量未定义。
	- `"boolean"`：表示变量是布尔类型。
	- `"number"`：表示变量是数值类型。
	- `"string"`：表示变量是字符串类型。
	- `"object"`：表示变量是对象类型，但不包括 `null`。
	- `"function"`：表示变量是函数类型。

* 需要注意的是，`typeof null` 返回 `"object"`，这是 JavaScript 早期版本的一个错误。此外，`typeof` 不能用于检测数组和日期等具有特定行为的对象类型。

### <font class="text-color-141" color="#ff9800">类型转换</font>
* 在 JavaScript 中，有以下的显式数据类型转换方法：

	1. `Number()` 方法可以将其他数据类型转换为数字类型。
	2. `String()` 方法可以将其他数据类型转换为字符串类型。
	3. `Boolean()` 方法可以将其他数据类型转换为布尔类型。
	4. `parseInt()` 和 `parseFloat()` 方法可以将字符串类型转换为数字类型。

```javascript
// 将字符串转换为数字
let numStr = "123";
let num = Number(numStr);

// 将数字转换为字符串
let num = 123;
let str = String(num);

// 将任意类型转换为布尔类型
let value = "hello";
let bool = Boolean(value);

// 将字符串转换为整数
let intStr = "123";
let int = parseInt(intStr);

// 将字符串转换为浮点数
let floatStr = "3.14";
let float = parseFloat(floatStr);
```
#### <font class="text-color-61" color="#03a9f4">Boolean()</font>
* `Boolean()` 是一个 JavaScript 中的内置函数，用于将一个值转换成一个布尔值。它的使用方法如下：
```javascript
Boolean(value);
// 其中 `value` 可以是任何数据类型的值，包括原始类型和对象类型。
```
* 当 `value` 为以下值时， `Boolean()` 的返回值为 `false`：

	- `false`
	- `0` 和 `-0`
	- `0n` 和 `-0n` (BigInt)
	- `null`
	- `undefined`
	- `NaN`
	- `''` (空字符串)

* 当 `value` 不为以上值时， `Boolean()` 的返回值为 `true`。
* if() 语句块中的值如果不是 Boolean 类型，会自动调用 Boolean() 函数

### <font class="text-color-141" color="#ff9800">undefined 注意</font>
* 在 JavaScript 中，当一个变量没有被赋值时，它的默认值为 `undefined`。`undefined` 是一个特殊的值，表示变量没有被赋值，或者被显式地赋值为 `undefined`。

* 例如，以下代码中的变量 `a` 和 `b` 没有被显式地赋值，因此它们的默认值都为 `undefined`：
```javascript
let a;
console.log(a); // 输出：undefined

let b;
console.log(b === undefined); // 输出：true
```
#### <font class="text-color-7" color="#03a9f4">null Nan undefined 区别</font>
* null、NaN 和 undefined 都是表示空或无效值的特殊值，但是它们之间有一些区别：

	- null 表示一个空对象引用，它是一个表示“无”的对象，可以用来表示变量的初始值或者表示函数调用无返回值。
	- NaN（Not a Number）表示不是数字的值，它是一个特殊的数字类型，用于表示数值运算中的非法操作或错误结果。
	- undefined 表示一个未定义的值，通常在声明变量但未初始化时默认赋值为 undefined。在函数调用时，如果函数没有返回值，其返回值默认为 undefined。

* 它们之间的区别在于：

	- null 是一个对象，表示空对象指针，可以认为它是一个特殊的对象值，但 null != undefined；
	- NaN 是一个数字类型，它是一个特殊的非数字值，可以通过 isNaN() 函数检测；
	- undefined 是一个表示“未定义”或“未赋值”的值，表示变量或属性没有被赋值或者不存在。

## <font class="text-color-121" color="#ffeb3b">控制语句</font>
### <font class="text-color-15" color="#ff9800">if 语句：</font>
```javascript
if (condition) {
  // 如果condition为true，执行这里的代码
} else {
  // 如果condition为false，执行这里的代码
}
```
### <font class="text-color-141" color="#ff9800">switch 语句：</font>
```javascript
switch (expression) {
  case value1:
    // 如果expression等于value1，执行这里的代码
    break;
  case value2:
    // 如果expression等于value2，执行这里的代码
    break;
  default:
    // 如果expression都不等于上述值，执行这里的代码
}
```
### <font class="text-color-141" color="#ff9800">while 语句：</font>
```javascript
while (condition) {
  // 只要condition为true，就一直执行这里的代码
}
```
### <font class="text-color-141" color="#ff9800">do...while 语句：</font>
```javascript
do {
  // 先执行一次，然后只要condition为true，就一直执行这里的代码
} while (condition);
```
### <font class="text-color-141" color="#ff9800">for 语句：</font>
```javascript
for (initialization; condition; increment) {
  // 每次循环执行这里的代码
}
```
### <font class="text-color-141" color="#ff9800">for...in 循环语句：</font>
* 用于遍历对象的属性。
```javascript
for (var key in obj) {
  // 只要 obj 中存在属性，就会遍历 obj 中的所有属性
}
```
* 其中 `obj` 是一个对象，`key` 是对象的属性名，循环遍历中的代码将针对每个属性执行一次。注意：`for...in` 遍历对象时是按属性名的顺序遍历的，但是顺序是不可靠的，并且不会遍历对象的原型链上的属性。(可以把对象当做一个数组来遍历 `obj[key]` )

* 如果遍历的是数组，则 `key` 是数组的下标

### <font class="text-color-141" color="#ff9800">for...of 循环语句：</font>
* 用于遍历可迭代对象（例如数组、字符串等）中的元素
```javascript
for (var element of iterable) {
  // 只要 iterable 中还有元素，就会遍历 iterable 中的所有元素
}
```
* 其中 `iterable` 是一个可迭代对象，`element` 是迭代器返回的元素，循环遍历中的代码将针对每个元素执行一次。注意：`for...of` 只能用于遍历可迭代对象，而不能用于遍历普通对象。


### <font class="text-color-141" color="#ff9800">break 语句：</font>
* 用于跳出循环或switch语句。
```javascript
for (var i = 0; i < 10; i++) {
  if (i == 5) {
    break; // 跳出循环
  }
}
```
### <font class="text-color-141" color="#ff9800">continue 语句：</font>
* 用于跳过循环中的某个代码块。
```javascript
for (var i = 0; i < 10; i++) {
  if (i == 5) {
    continue; // 跳过当前循环中i等于5的情况
  }
}
```
### <font class="text-color-141" color="#ff9800">return 语句：</font>
* 用于从函数中返回值。
```javascript
function add(a, b) {
  return a + b; // 返回a和b的和
}
```

### <font class="text-color-141" color="#ff9800">with 语句：</font>
* `with` 语句可以将一个对象的属性添加到作用域链的顶部，使得你可以直接访问该对象的属性，而无需使用对象名来引用属性。但是，由于它会改变作用域链，因此可能会引起一些意外的问题，所以在实际开发中，不建议使用 `with` 语句。
```javascript
with (object) {
   // 在这里，你可以直接访问 object 中的属性
}
```
* 其中，`object` 是要添加到作用域链中的对象。
* 例子：
```javascript
var person = {
   name: "张三",
   age: 18,
   sex: "男"
};

with (person) {
   console.log(name); // 输出 "张三"
   console.log(age); // 输出 18
   console.log(sex); // 输出 "男"
}
```
* 在 `with` 语句中，我们可以直接访问 `person` 对象的属性，而无需使用对象名 `person` 来引用属性。但是，由于 `with` 语句会改变作用域链，因此不建议在实际开发中使用。


## <font class="text-color-121" color="#ffeb3b">函数</font>
### <font class="text-color-15" color="#ff9800">语法格式</font>
```javascript
function functionName(parameters) {
  // 函数体
  return returnValue; // 可选的返回值
}
```
* 其中，`function` 是关键字，`functionName` 是函数名，`parameters` 是函数的参数列表，可以是多个参数，多个参数之间用逗号分隔。函数体中的语句可以访问参数和其他在函数范围内定义的变量。函数可以有一个可选的返回值，通过 `return` 关键字返回。如果没有返回值，或者没有 `return` 语句，则函数返回 `undefined`。函数可以在代码的任何位置被调用。

* JavaScript 函数还有一种语法格式，被称为函数表达式。它的语法格式如下：
```javascript
var functionName = function(parameters) {
  // 函数体
  return returnValue; // 可选的返回值
};
```
### <font class="text-color-15" color="#ff9800">空形参</font>
* 当 JavaScript 函数的形参没有赋值时，它们的值默认为 `undefined`。也就是说，如果调用函数时省略了某个参数，或者传递的参数不足函数期望的参数个数，那么这些参数的值将是 `undefined`。函数体中可以通过判断参数的值是否为 `undefined` 来处理这种情况，例如给参数设置默认值或者抛出异常等。
```javascript
function greet(name, message) {
  name = name || 'Stranger'; // 如果 name 的值为 undefined，则将其设置为 'Stranger'
  message = message || 'Hello'; // 如果 message 的值为 undefined，则将其设置为 'Hello'
  console.log(message + ', ' + name + '!');
}

greet(); // 输出 'Hello, Stranger!'
greet('Alice'); // 输出 'Hello, Alice!'
greet('Bob', 'Hi'); // 输出 'Hi, Bob!'
```
### <font class="text-color-141" color="#ff9800">函数覆盖</font>
* 在 JavaScript 中，函数名是函数的标识符，用于在代码中引用函数。如果在同一作用域内定义两个同名函数，那么后面的函数定义将会覆盖前面的函数定义，即后定义的函数会替代之前的函数。
```javascript
function add(a, b) {
  return a + b;
}

function add(a, b, c) {
  return a + b + c;
}

console.log(add(1, 2, 3)); // 输出：6
```

## <font class="text-color-13" color="#ffeb3b">运算符</font>

### <font class="text-color-15" color="#ff9800">|| 和 &&</font>
* `||` 是 JavaScript 中的逻辑或运算符，也称为 OR 运算符。它的作用是对两个操作数进行逻辑或运算，返回一个布尔值。

* 逻辑或运算符的运算规则如下：
	- 如果左操作数的值为真（即非零、非空、非 null、非 undefined、非 false），则返回左操作数的值；
	- 否则，返回右操作数的值。
---
* `&&` 是 JavaScript 中的逻辑与运算符，也称为 AND 运算符。它的作用是对两个操作数进行逻辑与运算，返回一个布尔值。

* 逻辑与运算符的运算规则如下：
	- 如果左操作数的值为假（即 false、0、''、null、undefined、NaN），则返回左操作数的值；
	- 否则，返回右操作数的值。

### <font class="text-color-141" color="#ff9800">== 和 ===</font>
* 在JavaScript中，`==` 和 `===` 是比较运算符，用于比较两个值是否相等。它们的主要区别在于类型比较的严格程度不同：

- `==` （等同运算符）执行弱类型比较，如果两个值的类型不同，它们会被转换为相同的类型，然后再进行比较。比较规则比较复杂，可能会导致一些奇怪的结果。比如，`null == undefined` 返回 `true`，但 `null === undefined` 返回 `false`。
- `===` （全等运算符）执行严格类型比较，只有当两个值的类型相同且值相等时才返回 `true`。如果类型不同，则直接返回`false`。

* 因此，如果要比较两个值是否相等，最好使用 `===`，因为它可以避免类型转换带来的问题。只有在确实需要进行弱类型比较时才使用 `==`。
---
### <font class="text-color-141" color="#ff9800">void</font>
* void运算符是一个一元运算符，用于执行一个表达式但不返回任何值。具体来说，void运算符对任何表达式进行求值，然后返回undefined。

* void运算符的主要用途是在JavaScript中创建“空链接”，即在\<a>标签中使用void(0)作为href属性值，以防止浏览器在用户单击链接时执行默认的行为（如跳转到新页面或重新加载页面）。例如：
```html
<a href="javascript:void(0)">点击此处不会跳转</a>
```
* 在上面的示例中，当用户单击链接时，JavaScript会执行一个空的语句，然后返回undefined，因此不会发生任何页面跳转。

* 另外，void运算符还可以用于创建立即执行函数表达式（IIFE）。例如，以下代码创建一个IIFE并立即执行它：
```javascript
void function() {
  // 这里是函数体
}();
```
* 在这个示例中，void运算符将函数表达式转换为一个语句，并在其后立即调用它。这样可以在不使用额外的变量的情况下执行一个函数，并且可以防止函数的返回值意外地影响到后续的代码执行。

#### <font class="text-color-7" color="#03a9f4">空链接</font>
* 空链接（void链接）是一种常见的HTML链接技巧，它将链接的目标地址设置为JavaScript的void运算符，即：
```html
<a href="javascript:void(0)">链接文本</a>
```
* 使用空链接的主要目的是防止页面跳转或刷新。当用户单击这种链接时，不会发生任何页面跳转或刷新，而只会执行JavaScript代码。这种技巧通常用于实现一些特殊的用户交互功能，例如展开/折叠区域、显示模态框等，而不希望用户在执行这些操作时离开当前页面。

* 使用空链接的另一个常见的用途是实现链接的默认行为。例如，有些链接需要在单击时执行一些JavaScript代码，然后继续跳转到其他页面。在这种情况下，可以将链接的href属性设置为JavaScript代码，然后在代码中执行需要的操作并返回true，以允许链接继续跳转。例如：
```html
<a href="javascript:doSomething();return true;">链接文本</a>
```
* 在这个示例中，当用户单击链接时，JavaScript会执行doSomething()函数，然后返回true，允许链接继续跳转到其他页面。如果doSomething()函数返回false，则链接不会跳转。


## <font class="text-color-13" color="#ffeb3b">类</font>
* 使用 class 关键字定义一个类
```javascript
class Person {
  name = "Tom"; // 定义在类的顶层的默认属性
  constructor(age) {
    this.age = age;
  }
  greet() {
    console.log(`My name is ${this.name}, I'm ${this.age} years old.`);
  }
}

const person = new Person(18);
person.greet(); // 输出 "My name is Tom, I'm 18 years old."
```
* 类的属性可以定义在constructor里面，也可以定义在类的顶层
### <font class="text-color-141" color="#ff9800">prototype</font>
* 每个对象都有一个称为 `prototype` 的隐藏属性，它指向其构造函数的原型对象。类和对象都是构造函数的实例，因此它们都有原型对象，即 `class.prototype` 和 `object.prototype`。

* 可以动态地给类添加属性和方法：
```javascript
Student.prototype.study = function() {
  console.log(this.name + '正在学习。');
};

const stu1 = new Student('小明', 18);
stu1.study(); // 输出：小明正在学习。
```


## <font class="text-color-13" color="#ffeb3b">String</font>
* 在JavaScript中，有以下3种方式创建字符串：
* 使用单引号或双引号包裹字符序列
```javascript
let str1 = 'Hello, world!';
let str2 = "Hello, world!";
```
* 使用模板字符串（template string），即使用反引号包裹字符序列，并使用 `${}` 拼接表达式
```javascript
let name = 'John';
let age = 30;
let str3 = `My name is ${name} and I'm ${age} years old.`;
```
* 使用 String() 构造函数创建字符串
```javascript
let str4 = String('Hello, world!');
```
### <font class="text-color-15" color="#ff9800">String 类型常用方法</font>

| 方法名        | 描述                                                                   |
| ------------- | ---------------------------------------------------------------------- |
| charAt()      | 返回指定位置的字符。                                                   |
| concat()      | 将两个或多个字符串拼接成一个新字符串。                                 |
| indexOf()     | 返回指定字符串在当前字符串中第一次出现的位置，如果没有找到则返回-1。   |
| lastIndexOf() | 返回指定字符串在当前字符串中最后一次出现的位置，如果没有找到则返回-1。 |
| match()       | 返回字符串中与正则表达式匹配的子串。                                   |
| replace()     | 替换字符串中的指定内容，并返回新字符串。                               |
| slice()       | 提取字符串中的一部分，并返回新字符串。                                 |
| split()       | 将字符串分割成字符串数组。                                             |
| substr()      | 从指定位置开始，截取指定长度的字符串。                                 |
| substring()   | 返回两个索引之间的子串。                                               |
| toLowerCase() | 将字符串转换为小写字母。                                               |
| toUpperCase() | 将字符串转换为大写字母。                                               |
| trim()        | 去除字符串首尾的空格。                                                 |
| startsWith()  | 判断字符串是否以指定的子串开头。                                       |
| endsWith()    | 判断字符串是否以指定的子串结尾。                                       |
| includes()    |   判断一个字符串是否包含另一个字符串。这个方法接收一个字符串参数，表示要查找的子串，如果该子串存在于原字符串中，返回 `true`，否则返回 `false`。                                                                     |

```javascript
let str = 'Hello, world!';

console.log(str.charAt(0)); // 输出：H
console.log(str.concat(' Goodbye!')); // 输出：Hello, world! Goodbye!
console.log(str.indexOf('world')); // 输出：7
console.log(str.match(/l+/g)); // 输出：['ll', 'l']
console.log(str.replace('world', 'John')); // 输出：Hello, John!
console.log(str.slice(0, 5)); // 输出：Hello
console.log(str.split(',')); // 输出：['Hello', ' world!']
console.log(str.substr(0, 5)); // 输出：Hello
console.log(str.substring(7, 12)); // 输出：world
console.log(str.toLowerCase()); // 输出：hello, world!
console.log(str.toUpperCase()); // 输出：HELLO, WORLD!
console.log(str.trim()); // 输出：Hello, world!
console.log(str.startsWith('Hello')); // 输出：true
console.log(str.endsWith('!')); // 输出：true
```
### <font class="text-color-15" color="#ff9800">String 属性</font>
* `length`：返回字符串的长度。
```javascript
let str = 'Hello, world!';
console.log(str.length); // 输出：13
```
* `prototype`：可以向 String 对象添加属性和方法。
```javascript
String.prototype.reverse = function () {
  return this.split('').reverse().join('');
}
let str = 'hello';
console.log(str.reverse()); // 输出：olleh

// 上述代码向 String 原型添加了一个 reverse() 方法，用于翻转字符串。
```
* `constructor`：返回用于创建字符串对象的函数。
```javascript
let str = 'Hello, world!';
console.log(str.constructor); // 输出：ƒ String() { [native code] }
```

## <font class="text-color-121" color="#ffeb3b">在 HTML 中嵌入 JavaScript 代码的3种方式</font>
### <font class="text-color-15" color="#ff9800">内联方式</font>
* 直接在 HTML 元素的属性中写入 JavaScript 代码
```html
<button onclick="alert('Hello World!')">点击我</button>
```
### <font class="text-color-141" color="#ff9800">内部嵌入方式</font>
* 在 HTML 文件中使用 `<script>` 标签包裹 JavaScript 代码
```html
<html>
  <head>
    <title>内部嵌入方式</title>
  </head>
  <body>
    <script>
      alert('Hello World!');
    </script>
  </body>
</html>
```
* 在 HTML 文件中，如果使用内联方式嵌入 JavaScript 代码，那么这些代码会被包含在 `<script>` 标签中，称为脚本块（Script Block）。脚本块中的程序会在页面加载时自动执行。

* 需要注意的是，脚本块中的程序遵守自上而下的顺序依次执行。也就是说，先定义的函数或变量在后面的程序中可以被调用，而后定义的函数或变量在前面的程序中是无法被调用的。因此，在编写脚本块时需要注意程序的顺序，以免出现调用错误或其他逻辑问题。

### <font class="text-color-141" color="#ff9800">外部引入方式</font>
* 将 JavaScript 代码单独写在一个文件中，然后在 HTML 文件中使用 `<script>` 标签引入外部文件。
```html
<html>
  <head>
    <title>外部引入方式</title>
  </head>
  <body>
    <script src="script.js"></script>
  </body>
</html>
```
* 其中，script.js 是包含 JavaScript 代码的文件名，该文件与 HTML 文件在同一个目录下。

* 注：外部引入方式的脚本块中的语句不会执行
---
需要注意的是，内联方式虽然简单，但是不易维护和扩展。在实际开发中，一般都会使用内部嵌入或外部引入方式来管理 JavaScript 代码。另外，为了提高页面的加载速度，通常会将 JavaScript 代码放在 HTML 文件的底部，或者在加载 JavaScript 文件时使用 `defer` 或 `async` 属性。

## <font class="text-color-121" color="#ffeb3b">事件</font>
* JavaScript 是一门事件驱动型的编程语言，即它的程序执行是基于事件的。事件可以是用户操作（如鼠标单击、键盘输入等），也可以是浏览器操作（如文档加载完成等）。当事件发生时，JavaScript 会调用与之相关联的函数（也称为事件处理程序），以响应事件。

* 在 JavaScript 中，有许多事件可供使用，如鼠标单击、键盘按下、页面滚动等等。每个事件都对应一个事件句柄，它是一个函数，用于响应特定的事件。对于鼠标单击事件来说，其对应的事件句柄叫作 onclick。事件句柄可以通过 HTML 标签的属性来指定，如下面的代码所示：
```html
<button onclick="alert('Hello World!')">点击我</button>
```
* 上面的代码中，我们使用 onclick 属性指定了一个事件句柄，它会在按钮被点击时弹出一个对话框。

* 在 JavaScript 中，`alert()` 函数用于在浏览器中弹出一个警告框，显示指定的消息。当 `alert()` 函数被调用时，JavaScript 引擎会暂停执行后面的程序，等待用户关闭警告框后再继续执行。这种暂停程序执行的行为称为阻塞（Blocking）。

* 因此，如果在 HTML 页面中的脚本块中使用 `alert()` 函数，会导致整个页面的加载被阻塞，直到用户关闭警告框。在使用 `alert()` 函数时，需要注意不要滥用，避免影响用户体验和页面性能。
---
### <font class="text-color-15" color="#ff9800">常用事件</font>
1. 鼠标事件
  
	  - `click`：单击事件。
	  - `dblclick`：双击事件。
	  - `mousedown`：鼠标按下事件。
	  - `mouseup`：鼠标释放事件。
	  - `mousemove`：鼠标移动事件。
	  - `mouseover`：鼠标悬停事件。
	  - `mouseout`：鼠标移出事件。
 
2. 键盘事件
  
	  - `keydown`：键盘按下事件。
	  - `keyup`：键盘释放事件。
	  - `keypress`：按下某个键后松开键盘事件。

3. 表单事件
  
	  - `submit`：表单提交事件。
	  - `reset`：表单重置事件。
	  - `focus`：元素获取焦点事件。
	  - `blur`：元素失去焦点事件。
	  - `change`：元素值改变事件。

4. 窗口事件
  
	  - `load`：文档加载完成事件。（整个html页面中所有元素全部加载完毕之后）
	  - `unload`：文档卸载事件。
	  - `resize`：窗口大小改变事件。
	  - `scroll`：滚动条滚动事件。

5. 其他事件
  
	  - `error`：脚本错误事件。
	  - `contextmenu`：右键菜单事件。
	  - `drag`：拖动事件。
	  - `drop`：拖放事件。

* 任何一个事件都会对应一个事件句柄，事件句柄是在事件前添加 on，事件句柄出现在一个标签的属性位置上。（事件句柄以属性的形式存在）

### <font class="text-color-15" color="#ff9800">注册事件的方式</font>

#### <font class="text-color-7" color="#03a9f4">HTML 属性方式</font>
* 可以在 HTML 标签中通过添加事件属性来注册事件
```html
<button onclick="myFunction()">Click me</button>
```
* 对于当前程序来说，myFunction() 函数被称为回调函数（callback 函数）

#### <font class="text-color-7" color="#03a9f4">DOM 0 级事件处理程序</font>
* 可以通过 JavaScript 代码来注册事件
```html
<button id="myButton">Click me</button>
<script>
  var button = document.getElementById("myButton");
  button.onclick = function() {
    alert("Hello World!");
  };
</script>
```
* `getElementById` 是 JavaScript DOM (文档对象模型) API 中的一个方法，用于通过元素的 ID (HTML 属性) 获取对该元素的引用。该方法通常用于从 HTML 文档中获取特定元素的引用，以便通过 JavaScript 对其进行操作，例如更改元素的样式、属性或内容。`getElementById` 方法返回一个对象，该对象表示具有指定 ID 的 HTML 元素，如果找不到具有指定 ID 的元素，则返回 `null`。该方法只能在浏览器中运行，因为它是浏览器的内置 DOM API。

#### <font class="text-color-7" color="#03a9f4">DOM 2 级事件处理程序</font>
* DOM 2 级事件处理程序是针对 DOM Level 2 规范的一种事件处理方式，相对于 DOM 0 级和 DOM 1 级事件处理，它具有更加标准化、规范化的特点，支持事件流的阶段、事件冒泡、事件捕获等特性。

* 通过 addEventListener() 方法添加事件处理程序
```html
<button id="btn">Click me</button>

<script>
  var btn = document.getElementById("btn");
  btn.addEventListener("click", function() {
    alert("click");
  }, false);
</script>
```
* 其中，第一个参数为事件类型，第二个参数为事件处理程序，第三个参数表示事件流的阶段，为可选参数，默认为冒泡阶段。
---
### <font class="text-color-15" color="#ff9800">js代码主动触发事件</font>
* 可以用 js 代码主动出发 html 元素的事件
```html
<script>
	// 主动出发 click 事件
	document.getElementById("myButton").click()
</script>
用户名<input type="button" name="按钮" id="myButton">
```

### <font class="text-color-15" color="#ff9800">代码执行顺序</font>
* 当浏览器加载文档时，它会逐个读取HTML、CSS和JavaScript代码。如果在JavaScript代码执行之前，HTML元素还没有完全加载，那么代码中引用的元素将无法被正确识别和操作。

* 例子：
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
</head>
<body>
    <script>
        window.onload = function () {
            document.getElementById("hello1").onclick = function () {
                window.alert("hi there!")
            }
        }
    </script>

    <input type="button" value="hello" id="hello1">
</body>
</html>
```
* 在这段代码中，`onload` 的作用是确保页面的所有元素都已加载完成后再执行相应的JavaScript代码。

* `window.onload` 事件会等到文档中所有的元素都被完全加载后才会触发。一旦 `onload` 事件被触发，就会执行事件处理程序，其中的JavaScript代码会将一个单击事件处理程序添加到按钮 `hello1` 上。这样，当用户单击该按钮时，浏览器将执行处理程序，弹出一个包含"hi there!"消息的警告框。由于 `onload` 事件的存在，JavaScript代码的执行会被延迟，直到所有元素都已加载完成，从而确保代码能够正确地执行。


## <font class="text-color-121" color="#ffeb3b">数组</font>
* <a href="https://www.runoob.com/jsref/jsref-obj-array.html">Array 对象文档</a>
### <font class="text-color-15" color="#ff9800">创建数组</font>
* 字面量语法（Literal Syntax）：使用方括号 `[ ]` 来定义一个新的数组，并用逗号 `,` 分隔各个元素。
```javascript
var arr1 = []; // 定义一个空数组
var arr2 = [1, 2, 3]; // 定义一个包含3个元素的数组
var arr3 = ["apple", "banana", "orange"]; // 定义一个包含3个字符串元素的数组
```
* `Array` 构造函数（Constructor）：使用 `new` 关键字和 `Array` 构造函数来创建一个新的数组。
```javascript
var arr1 = new Array(); // 定义一个空数组
var arr2 = new Array(1, 2, 3); // 定义一个包含3个元素的数组
var arr3 = new Array("apple", "banana", "orange"); // 定义一个包含3个字符串元素的数组
var arr4 = new Array(5); // 定义一个包含5个 undefined 元素的数组
```
* `Array.of()` 静态方法：使用 `Array.of()` 方法来创建一个包含任意数量元素的新数组。
```javascript
var arr1 = Array.of(); // 定义一个空数组
var arr2 = Array.of(1, 2, 3); // 定义一个包含3个元素的数组
var arr3 = Array.of("apple", "banana", "orange"); // 定义一个包含3个字符串元素的数组
```
* `Array.from()` 静态方法：使用 `Array.from()` 方法将类数组对象或可迭代对象转换成一个新数组。
```javascript
var arr1 = Array.from("abc"); // 将字符串转换成包含3个字符元素的数组 ["a", "b", "c"]
var arr2 = Array.from({ length: 3 }, (value, index) => index + 1); // 将类数组对象转换成包含3个数字元素的数组 [1, 2, 3]
var arr3 = Array.from(new Set([1, 2, 3])); // 将 Set 对象转换成包含3个数字元素的数组 [1, 2, 3]
```
---
### <font class="text-color-15" color="#ff9800">数组遍历</font>
* `for` 循环：使用 `for` 循环语句，以数组长度为循环条件，遍历数组中的每个元素。
```javascript
var arr = [1, 2, 3];
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```
* `for...of` 循环：使用 `for...of` 循环语句，以数组对象为循环条件，遍历数组中的每个元素。
```javascript
var arr = [1, 2, 3];
for (var item of arr) {
  console.log(item);
}
```
* `forEach()` 方法：使用 `forEach()` 数组方法，以回调函数作为参数，遍历数组中的每个元素。
```javascript
var arr = [1, 2, 3];
arr.forEach(function(item) {
  console.log(item);
});
```
* `map()` 方法：使用 `map()` 数组方法，以回调函数作为参数，遍历数组中的每个元素，并返回一个新的数组。
```javascript
var arr = [1, 2, 3];
var newArr = arr.map(function(item) {
  return item * 2;
});
console.log(newArr); // 输出 [2, 4, 6]
```

## <font class="text-color-121" color="#ffeb3b">DOM 编程</font>

### <font class="text-color-15" color="#ff9800">DOM 对象</font>
* DOM（Document Object Model）对象是浏览器将 HTML、XML 和 SVG 等文档解析为树形结构之后，将其映射为一组对象的 API（应用程序接口）。在 DOM 树中，每个 HTML 元素、文本和属性都是一个对象，可以使用 JavaScript 脚本操作这些对象，例如添加、删除或更改它们的属性、内容或者调用对象的方法。通过使用 DOM，JavaScript 可以修改页面上的文本和图像、创建新的 HTML 元素、更改元素的样式、设置元素的事件处理程序等等。因此，DOM 是在 Web 开发中非常重要的一部分。

* <a href="https://www.runoob.com/jsref/dom-obj-form.html">DOM 对象文档</a>

### <font class="text-color-15" color="#ff9800">获取和修改标签属性</font>
* 获取HTML标签的属性可以使用DOM API中的属性获取方法，例如`getElementById`、`getElementsByTagName`等，来获取对应的HTML元素对象，然后使用该对象的属性来获取对应的属性值。例如，`document.getElementById('myId').value`可以获取ID为`myId`的输入框的当前值。

* 修改HTML标签的属性可以使用DOM API中的属性设置方法，例如`setAttribute`、`style`属性等，来修改对应的HTML元素的属性值。例如，`document.getElementById('myId').setAttribute('value', 'new value')`可以将ID为`myId`的输入框的值设置为`new value`。

* 需要注意的是，如果HTML标签的属性是内联样式（inline style）的形式，可以使用元素对象的`style`属性来获取或修改。例如，`document.getElementById('myId').style.color = 'red'`可以将ID为`myId`的元素的文本颜色设置为红色。

* 例子
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
</head>
<body>
    <script>
        window.onload = function (){
            document.getElementById("defaultButton").onclick = function(){
                // 获取标签对象
                let msg1 = document.getElementById("msg1")
                // 修改标签的属性
                msg1.readOnly = true
                msg1.value = "default message"
            }
        }
    </script>

    <input type="text" name="msg" id="msg1">
    <input type="button" value="default" id="defaultButton">
</body>
</html>
```

### <font class="text-color-15" color="#ff9800">捕捉按键</font>
* 可以通过event对象的keyCode属性来获取用户按下的键的编码值，从而判断具体按下了哪个键。
```javascript
document.addEventListener("keydown", function(event) {
  switch (event.keyCode) {
    case 37: // 左箭头
      moveLeft();
      break;
    case 38: // 上箭头
      moveUp();
      break;
    case 39: // 右箭头
      moveRight();
      break;
    case 40: // 下箭头
      moveDown();
      break;
    case 13: // 回车键
      submitForm();
      break;
    default:
      // 其他按键
      break;
  }
});
```

* html 例子
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
</head>
<body>
    <script>
        function handleEnterKey(event) {
            if (event.keyCode === 13) {
                var inputBox = document.getElementById("inputBox");
                window.alert("你输入的是：" + inputBox.value);
                inputBox.value = "";
            }
        }
    </script>

    <label for="inputBox">输入：</label>
    <input type="text" id="inputBox" onkeydown="handleEnterKey(event)">
</body>
</html>
```
* 常用按键编号
```
- Backspace：8
- Tab：9
- Enter：13
- Shift：16
- Ctrl：17
- Alt：18
- Pause/Break：19
- Caps Lock：20
- Esc：27
- Space：32
- Page Up：33
- Page Down：34
- End：35
- Home：36
- Left Arrow：37
- Up Arrow：38
- Right Arrow：39
- Down Arrow：40
- Insert：45
- Delete：46
- 0-9键（顶部数字键盘和主键盘）：48-57
- A-Z键：65-90
- 左Win键：91
- 右Win键：92
- 上下文菜单键（右键）：93
- 小键盘0-9键：96-105
- 小键盘加号：107
- 小键盘减号：109
- 小键盘乘号：106
- 小键盘除号：111
- F1-F12键：112-123
- 分号：186
- 等于号：187
- 逗号：188
- 减号：189
- 句点：190
- 斜杆：191
- 反斜杠：220
- 单引号：222
```
### <font class="text-color-15" color="#ff9800">获取和修改文本框内容</font>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
</head>
<body>
    <script>
        window.onload = function(){
            document.getElementById("button1").onclick = function(){
                // 获取文本框对象
                let text = document.getElementById("text1")
                alert(text.value)
                text.value = "默认信息";
            }
        }
    </script>

    <input type="text" id="text1">
    <input type="button" value="提交" id="button1">
    <br><br><br><br><br>

    <!-- onblur 为失去焦点事件 -->
    <input type="text" onblur="alert(this.value)">
</body>
</html>
```
### <font class="text-color-15" color="#ff9800">innerText 和 innerHTML</font>
* innerText和innerHTML都是DOM元素的属性，用于获取或设置元素的内容。

* innerText 会把后面的内容当作字符串（即使是html代码）

* innerHTML 会把后面的内容当作 html 代码解释并执行
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
    <style type="text/css">
        #myDiv{
            background-color: lightblue;
            border: 2px black solid;
        }
    </style>
</head>
<body>
    <script>
        window.onload = function (){
            document.getElementById("myButton").onclick = function(){
                var myDiv = document.getElementById("myDiv");

                // 获取文本内容
                var textContent = myDiv.innerText; // "Hello, world!"
                var htmlContent = myDiv.innerHTML; // "<p>Hello, <strong>world</strong>!</p>"

                // 修改元素内容
                myDiv.innerText = "Goodbye, world!";
                myDiv.innerHTML = "<p>Goodbye, <strong>world</strong>!</p>";
            }
        }
    </script>

    <div id="myDiv">
        <p>Hello, <strong>world</strong>!</p>
        <input type="button" value="修改" id="myButton">
    </div>
</body>
</html>
```
### <font class="text-color-15" color="#ff9800">示例</font>

#### <font class="text-color-61" color="#03a9f4">注册界面验证</font>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
    <style type="text/css">
        /* 为表单设置样式 */
        form {
            max-width: 400px;
            margin: 0 auto;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px #ccc;
        }

        /* 为输入框设置样式 */
        .input {
            display: block;
            width: 100%;
            height: 40px;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: 16px;
            box-sizing: border-box;
        }

        /* 为错误提示信息设置样式 */
        .span1 {
            display: block;
            font-size: 12px;
            color: red;
            margin-top: 5px;
        }

        /* 为重置按钮设置样式 */
        #resetButton {
            display: inline-block;
            width: 100px;
            height: 40px;
            margin-top: 20px;
            margin-right: 10px;
            background-color: #f44336;
            border: none;
            border-radius: 5px;
            color: #fff;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        /* 当鼠标悬停在按钮上时，更改其背景颜色 */
        #resetButton:hover {
            background-color: #999;
        }
        #submitButton:hover {
            background-color: green;
        }
    </style>

</head>
<body bgcolor="silver">
    <script>
        window.onload = function (){

            // 获取用户名文本框
            let username = document.getElementById("username")
            // 获取用户名错误信息 span
            let usernameErrorSpan = document.getElementById("usernameError")
            // 用户名格式是否正确标记位
            let illegalUsername = true
            // 用户名文本框绑定 blur 事件
            username.onblur = function () {
                let name = username.value
                name = name.trim()
                if(!Boolean(name)){
                    // 空字符串
                    illegalUsername = true
                    usernameErrorSpan.innerText = "用户名不能为空"
                }else {
                    let pattern = /^[a-zA-Z0-9_-]{4,20}$/
                    if(!pattern.test(name)){
                        // 用户名格式错误
                        alert("用户名格式不正确：用户名的长度通常应在4到20个字符之间,且仅包含字母、数字、下划线和连字符")
                        illegalUsername = true
                        usernameErrorSpan.innerText = "用户名格式错误"
                    }else {
                        // 用户名格式正确
                        illegalUsername = false
                        usernameErrorSpan.innerHTML = "<font color='#a0522d'>√</font>"
                    }
                }
            }
            // 用户名文本框绑定 focus 事件
            username.onfocus = function () {
                if(illegalUsername) username.value = ""
            }


            // 获取密码框
            let userpwd = document.getElementById("userpwd")
            // 获取密码错误信息 span
            let userpwdErrorSpan = document.getElementById("userpwdError")
            // 密码格式是否正确标记位
            let illegalUserpwd = true
            // 密码框绑定 blur 事件
            userpwd.onblur = function () {
                let pwd = userpwd.value
                if(!Boolean(pwd)){
                    // 空字符串
                    illegalUserpwd = true
                    userpwdErrorSpan.innerText = "密码不能为空"
                }else {
                    let pattern = /^[a-zA-Z0-9_-]{6,16}$/
                    if(!pattern.test(pwd)){
                        // 密码格式错误
                        alert("密码格式不正确：密码为长度在6到16个字符之间的由字母、数字、下划线和连字符组成的字符串")
                        illegalUserpwd = true
                        userpwdErrorSpan.innerText = "密码格式错误"
                    }else {
                        // 密码格式正确
                        illegalUserpwd = false
                        userpwdErrorSpan.innerHTML = "<font color='#a0522d'>√</font>"
                    }
                }
            }
            // 密码框绑定 focus 事件
            userpwd.onfocus = function () {
                if(illegalUserpwd) userpwd.value = ""
            }


            // 获取确认密码框
            let confirmpwd = document.getElementById("confirmpwd")
            // 获取确认密码错误信息 span
            let confirmErrorSpan = document.getElementById("confirmError")
            // 确认密码否正确标记位
            let illegalConfirmpwd = true
            // 确认密码框绑定 blur 事件
            confirmpwd.onblur = function () {
                let confirme = confirmpwd.value
                if(!Boolean(confirme)){
                    // 空字符串
                    illegalConfirmpwd = true
                    confirmErrorSpan.innerText = "密码不能为空"
                }else {
                    if(!(confirme === userpwd.value)){
                        illegalConfirmpwd = true
                        confirmErrorSpan.innerText = "确认密码与输入密码不匹配"
                    }else {
                        illegalConfirmpwd  = false
                        confirmErrorSpan.innerHTML = "<font color='#a0522d'>√</font>"
                    }
                }
            }
            // 密码框绑定 focus 事件
            confirmpwd.onfocus = function () {
                if(illegalConfirmpwd) confirmpwd.value = ""
            }

            // 获取邮箱输入框
            let email = document.getElementById("email")
            // 获取邮箱输入框错误信息 span
            let emailErrorSpan = document.getElementById("emailError")
            // 确认邮箱输入框是否正确标记位
            let illegalEmail = true
            // 密码框绑定 blur 事件
            email.onblur = function () {
                let emailInput = email.value
                if(!Boolean(emailInput)){
                    // 空字符串
                    illegalEmail = true
                    emailErrorSpan.innerText = "邮箱不能为空"
                }else {
                    let pattern = /^[a-zA-Z0-9_-]+@[a-zA-Z0-9_-]+(\.[a-zA-Z0-9_-]+)+$/
                    if(!pattern.test(emailInput)){
                        // 邮箱格式错误
                        alert("邮箱格式不正确")
                        illegalEmail = true
                        emailErrorSpan.innerText = "邮箱格式错误"
                    }else {
                        // 邮箱格式正确
                        illegalEmail = false
                        emailErrorSpan.innerHTML = "<font color='#a0522d'>√</font>"
                    }
                }
            }
            // 邮箱输入框绑定 focus 事件
            email.onfocus = function () {
                if(illegalEmail) email.value = ""
            }

            // 重置键绑定 click 事件
            document.getElementById("resetButton").onclick = function () {
                usernameErrorSpan.innerText = ""
                userpwdErrorSpan.innerText = ""
                confirmErrorSpan.innerText = ""
                emailErrorSpan.innerText = ""
                illegalUsername = true
                illegalUserpwd = true
                illegalConfirmpwd = true
                illegalEmail = true
            }

            // 注册键绑定 click 事件
            document.getElementById("submitButton").onclick = function () {
                // js 代码主动触发事件
                username.focus();
                username.blur();
                userpwd.focus();
                userpwd.blur();
                confirmpwd.focus();
                confirmpwd.blur();
                email.focus();
                email.blur();
                // 获取 form 对象
                let userFormElt = document.getElementById("userForm")
                if(illegalUsername || illegalUserpwd || illegalConfirmpwd || illegalEmail){
                    alert("无法注册，请检查是否还有未完成项")
                }else{
                    alert("注册成功")
                    userFormElt.submit()
                }
            }
        }
    </script>

    <div id="myDiv1">
        <!--表单-->
        <form action="http://localhost:8080/stub/save" method="get" id="userForm">
            <header>欢迎注册！</header>
            <br>
            用户名<input type="text" name="username" id="username" class="input"> <span id="usernameError" class="span1"></span> <br><br>
            密码<input type="password" name="userpwd" id="userpwd" class="input"> <span id="userpwdError" class="span1"></span> <br><br>
            确认密码<input type="password" id="confirmpwd" class="input"> <span id="confirmError" class="span1"></span> <br><br>
            邮箱<input type="text" id="email" class="input"> <span id="emailError" class="span1"></span> <br><br>
            <input type="button" value="注册" id="submitButton" class="input"> <br><br>
            <input type="reset" value="重置" id="resetButton" style="position:absolute;left:33%;"><br><br>
        </form>
    </div>
</body>
</html>
```
#### <font class="text-color-61" color="#03a9f4">复选框全选和取消</font>
1. 首先，在 HTML 中给复选框全选和取消添加一个 `id` 属性，方便 JavaScript 代码获取 DOM 元素。
2. 获取全选按钮和所有的复选框元素的 DOM 对象。
3. 给全选按钮添加一个点击事件监听器，当全选按钮被点击时，遍历所有的复选框元素，将它们的 `checked` 属性设置为全选按钮的状态。
4. 给每个复选框元素添加一个点击事件监听器，当某个复选框元素被点击时，检查所有复选框的选中状态，如果全部选中，则将全选按钮的 `checked` 属性设置为 `true`，否则设置为 `false`。
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Login Page</title>
</head>
<body>
    <script>
        window.onclick = function () {
            // 获取全选按钮和所有的复选框元素
            var checkAll = document.getElementById('check-all');
            var checkboxes = document.getElementsByClassName('checkbox-item');

            // 给全选按钮添加一个点击事件监听器
            checkAll.addEventListener('click', function() {
                for (var i = 0; i < checkboxes.length; i++) {
                    checkboxes[i].checked = this.checked;
                }
            });

            // 给每个复选框元素添加一个点击事件监听器
            for (var i = 0; i < checkboxes.length; i++) {
                checkboxes[i].addEventListener('click', function() {
                    var allChecked = true;
                    for (var j = 0; j < checkboxes.length; j++) {
                        if (!checkboxes[j].checked) {
                            allChecked = false;
                            break;
                        }
                    }
                    checkAll.checked = allChecked;
                });
            }

        }
    </script>

    <label><input type="checkbox" class="check-all" id="check-all">全选</label>
    <label><input type="checkbox" class="checkbox-item">复选框1</label>
    <label><input type="checkbox" class="checkbox-item">复选框2</label>
    <label><input type="checkbox" class="checkbox-item">复选框3</label>
</body>
</html>
```
#### <font class="text-color-61" color="#03a9f4">下拉列表获取选项中的value</font>
* 监听下拉列表的 `change` 事件，获取 value
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Login Page</title>
</head>
<body>
    <select id="mySelect">
        <option value="" selected>--请选择--</option>
        <option value="apple">苹果</option>
        <option value="banana">香蕉</option>
        <option value="orange">橙子</option>
    </select>

    <script>
        var selectElement = document.getElementById("mySelect");
        selectElement.addEventListener("change", function () {
            var selectedValue = selectElement.value;
            alert(selectedValue); // 输出选中项的 value 值
        });
    </script>
</body>
</html>
```
#### <font class="text-color-61" color="#03a9f4">监听输入框（购物车例子）</font>
* 监听输入框的 `change` 事件，实时改变结果
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>购物车</title>
    <script>
        function calculateTotal() {
            var total = 0;
            var items = document.getElementsByClassName("item");

            for (var i = 0; i < items.length; i++) {
                var item = items[i];
                var price = parseFloat(item.getElementsByClassName("price")[0].textContent);
                var quantity = parseInt(item.getElementsByClassName("quantity")[0].value);
                var subtotal = price * quantity;
                item.getElementsByClassName("subtotal")[0].textContent = subtotal.toFixed(2);
                total += subtotal;
            }

            document.getElementById("total").textContent = total.toFixed(2);
        }
    </script>
</head>
<body>
<h1>购物车</h1>

<table>
    <thead>
    <tr>
        <th>商品名称</th>
        <th>单价</th>
        <th>数量</th>
        <th>小计</th>
    </tr>
    </thead>
    <tbody>
    <tr class="item">
        <td>苹果</td>
        <td class="price">5.00</td>
        <td><input type="number" class="quantity" value="1" onchange="calculateTotal()"></td>
        <td class="subtotal">5.00</td>
    </tr>
    <tr class="item">
        <td>香蕉</td>
        <td class="price">3.50</td>
        <td><input type="number" class="quantity" value="2" onchange="calculateTotal()"></td>
        <td class="subtotal">7.00</td>
    </tr>
    <tr class="item">
        <td>橙子</td>
        <td class="price">4.20</td>
        <td><input type="number" class="quantity" value="3" onchange="calculateTotal()"></td>
        <td class="subtotal">12.60</td>
    </tr>
    </tbody>
    <tfoot>
    <tr>
        <th colspan="3">总计：</th>
        <td id="total">24.60</td>
    </tr>
    </tfoot>
</table>
</body>
</html>
```
## <font class="text-color-121" color="#ffeb3b">BOM 编程</font>
* <a href="https://www.runoob.com/jsref/obj-window.html">window 对象文档</a>
### <font class="text-color-141" color="#ff9800">打开和关闭窗口</font>
* `window.open`和`window.close`都是JavaScript中用于操作浏览器窗口的方法，其中`window.open`用于打开一个新的浏览器窗口，而`window.close`用于关闭一个已经打开的浏览器窗口。

* `window.open`方法语法如下：
```javascript
window.open(url, name, specs, replace);
```
* 其中，`url`表示要打开的网页地址；`name`表示新窗口的名称，可以是空字符串或者一个唯一的名称；`specs`表示新窗口的特性，比如窗口大小、是否有滚动条等；`replace`表示是否用新打开的页面替换当前页面的历史记录，即是否将新页面加入浏览器的历史记录中。

* 例如，下面的代码会在新窗口中打开`http://www.example.com`网页：
```javascript
window.open('http://www.example.com', '_blank');
```
* `window.close`方法可以关闭一个已经打开的窗口。如果窗口是由JavaScript打开的，那么只有该窗口中打开的页面才能关闭窗口。例如，下面的代码可以关闭当前窗口：
```javascript
window.close();
```
* 需要注意的是，由于浏览器的安全机制限制，JavaScript无法关闭非由JavaScript打开的窗口，例如通过浏览器地址栏或者其他程序打开的窗口。此外，在一些浏览器中，如果弹出窗口被浏览器的弹出窗口拦截器拦截，JavaScript也无法关闭该窗口。

### <font class="text-color-141" color="#ff9800">确认窗口（confirm）</font>
* `window.confirm` 是 JavaScript 提供的一个函数，用于在浏览器中弹出一个确认对话框，通常用于确认某个操作是否继续执行。该函数会返回一个布尔值，如果用户点击确认，则返回 `true`，否则返回 `false`。
```html
<button onclick="confirmDelete()">删除</button>

<script>
function confirmDelete() {
  var confirmed = window.confirm("确定要删除吗？");
  if (confirmed) {
    // 执行删除操作
    console.log("执行删除操作");
  } else {
    console.log("取消删除");
  }
}
</script>
```
* 当用户点击按钮时，会弹出一个确认对话框，询问用户是否要删除。如果用户点击确认，则会执行删除操作；否则会输出 "取消删除"。

### <font class="text-color-141" color="#ff9800">history</font>
* `window.history` 是 JavaScript 中表示浏览器历史记录的 API，通过该 API 可以操作用户在浏览器中访问过的网页的历史记录。
	- history.back()：相当于点击浏览器的“返回”按钮，返回上一页。
	- history.forward()：相当于点击浏览器的“前进”按钮，前往下一页。
	- history.go(n)：相当于点击浏览器的“前进”或“返回”按钮n次，n可以是正数（前进）或负数（返回）。
	- history.length：返回浏览器历史记录中的页面数。
	
* 示例
```html
<!DOCTYPE html>
<html>
<head>
	<title>History Example</title>
</head>
<body>
	<button onclick="goBack()">Back</button>
	<button onclick="goForward()">Forward</button>
	<script>
		function goBack() {
			window.history.go(-1);
		}
		function goForward() {
			window.history.go(1);
		}
	</script>
</body>
</html>
```

### <font class="text-color-141" color="#ff9800">location</font>
* `window.location` 是一个包含当前窗口网址的对象，它可以用于获取或设置当前窗口的 URL 地址。通过修改 `window.location` 属性，可以改变当前窗口的 URL 地址并导航到新的页面。

* 例如，我们可以使用以下代码在当前窗口中导航到另一个页面：
```javascript
window.location.href = "http://www.example.com";
```
* 这会将当前窗口的 URL 地址更改为 `http://www.example.com` 并加载该网页。

* 我们还可以使用其他属性来获取或设置当前页面的不同部分，如 `window.location.hostname`、`window.location.pathname`、`window.location.protocol` 等。

* 例如，我们可以使用以下代码在控制台中打印当前页面的主机名：
```javascript
console.log(window.location.hostname);
```
* 这会将当前页面的主机名打印到控制台上。

* 还可以通过 `window.location.reload()` 方法来重新加载当前页面。

* 例如，我们可以使用以下代码重新加载当前页面：
```javascript
window.location.reload();
// 这会重新加载当前页面并显示最新内容。
```

### <font class="text-color-141" color="#ff9800">top 和 self</font>
* 在浏览器中，`window.top` 和 `window.self` 是 `Window` 对象的属性，它们分别代表浏览器的最顶层窗口和当前窗口。以下是它们的详细解释：

	- `window.top` 属性返回最顶层窗口，即浏览器窗口。如果当前窗口不是浏览器窗口，它会递归向上返回最顶层窗口。如果在 iframe 中使用，则返回包含 iframe 的最顶层窗口。
	- `window.self` 属性返回当前窗口，即当前的 `Window` 对象。

* 示例：如果当前窗口不是顶级窗口，则将当前窗口设置为顶级窗口
```javascript
if (window.top !== window.self) {
  window.top.location.href = window.self.location.href;
}
```


## <font class="text-color-121" color="#ffeb3b">正则表达式</font>
* 正则表达式（Regular Expression）是一种用于描述字符模式的表达式，通常被用来匹配、搜索、替换特定模式的文本。正则表达式在各种编程语言和文本编辑器中都得到了广泛的应用，是处理文本的重要工具之一。

* 正则表达式包含一系列字符和特殊符号，可以用来匹配字符串中的某个部分或整个字符串，匹配时可以考虑字符出现的位置、数量、范围等多种因素，具有很强的灵活性和表达能力。

* <a href="https://www.runoob.com/jsref/jsref-obj-regexp.html">javadcript 正则表达式</a>

### <font class="text-color-141" color="#ff9800">正则表达式创建</font>
1. 通过字面量方式创建
	- 可以使用反斜杠（\）将正则表达式分为两行，可以提高可读性。
	- 当 `pattern` 不为正则表达式时（普通字符串），`flag` 不能为 `m`
```javascript
let regex = /pattern/flags;
```
2. 通过RegExp构造函数创建
	通过RegExp构造函数可以动态地生成正则表达式，可以在运行时传递正则表达式的参数。
```javascript
let regex = new RegExp("pattern",flags);
```


#### <font class="text-color-7" color="#03a9f4">QQ号</font>
* QQ号是一个5~11位的数字字符串，一般采用以下正则表达式来匹配：
```javascript
var regex = /^[1-9][0-9]{4,10}$/
```
- `^` 表示字符串的开始；
- `[1-9]` 表示第一个数字不能为0；
- `[0-9]` 表示数字；
- `{4,10}` 表示数字长度最少为4位，最多为10位；
- `$` 表示字符串的结束。

#### <font class="text-color-61" color="#03a9f4">邮箱</font>
```javascript
var regex = /^([a-zA-Z0-9_\.-]+)@([\da-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/
```
* 该正则表达式可以匹配大部分常见的邮箱地址，其中：

	- `^` 表示字符串的开始；
	- `([a-zA-Z0-9_\.-]+)` 匹配用户名，其中：
	  - `[]` 表示字符集合；
	  - `+` 表示匹配前面的字符集合一次或多次；
	  - `a-z` 和 `A-Z` 表示匹配大小写字母；
	  - `0-9` 表示匹配数字；
	  - `_` 表示匹配下划线；
	  - `\.` 表示匹配点号，需要用反斜杠转义；
	- `@` 表示匹配邮箱地址中的@符号；
	- `([\da-zA-Z\.-]+)` 匹配邮箱的域名，其中：
	  - `\d` 表示数字；
	  - `a-z` 和 `A-Z` 表示匹配大小写字母；
	  - `.` 表示匹配点号；
	  - `-` 表示匹配连字符；
	  - `+` 表示匹配前面的字符集合一次或多次；
	- `\.` 表示匹配邮箱地址中的点号，需要用反斜杠转义；
	- `([a-zA-Z\.]{2,6})` 匹配邮箱的顶级域名，其中：
	  - `{2,6}` 表示匹配前面的字符集合 2 到 6 次；
	- `$` 表示字符串的结束。
---
### <font class="text-color-141" color="#ff9800">test()</font>
* 正则表达式对象的test()方法是用来测试一个字符串是否符合正则表达式的规则的，其语法如下：
```javascript
regexObj.test(str)
```
* 其中，regexObj表示一个正则表达式对象，str表示要测试的字符串。test()方法返回一个布尔值，表示字符串是否符合正则表达式的规则。如果字符串符合规则，则返回true；否则返回false。

### <font class="text-color-141" color="#ff9800">match()</font>
* match()方法，可以用来进行正则表达式的匹配。match()方法接收一个正则表达式作为参数，返回匹配结果。

* match()方法有两种使用方式，一种是通过字符串对象调用，另一种是通过RegExp对象调用。
```javascript
// 1. 通过字符串对象调用
string.match(regexp);
// 2. 通过RegExp对象调用
regexp.match(string);
```
* 示例
```javascript
let str = "The quick brown fox jumps over the lazy dog";
let pattern = /the/gi;
let regexp = new RegExp(pattern);
let matches = regexp.match(str);
console.log(matches); // 输出 ["The", "the"]
```

#### <font class="text-color-7" color="#03a9f4">邮箱格式验证例子</font>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
    <style type="text/css">
        #myDiv1{
            background-color: lightblue;
            border: 2px black solid;
        }
        #myDiv2{
            background-color: silver;
            border: 2px black solid;
        }
    </style>
</head>
<body>
    <script>
        window.onload = function (){
            // 给按钮绑定点击事件
            document.getElementById("myButton").onclick = function(){
                // 获取文本框对象
                let textBox = document.getElementById("myInput")
                // 获取输入的内容
                let msg = textBox.value
                msg = msg.trim()
                // 创建正则表达式对象
                let regex = /^([a-zA-Z0-9_\.-]+)@([\da-zA-Z\.-]+)\.([a-zA-Z\.]{2,6})$/
                // 测试
                let result = regex.test(msg)
                // 返回结果
                if(result) document.getElementById("myDiv2").innerText = "邮箱格式正确!"
                else document.getElementById("myDiv2").innerText = "邮箱格式不正确!"
            }
            // 给按文本框绑定聚焦事件
            document.getElementById("myInput").onfocus = function (){
                // 清空结果区域
                document.getElementById("myDiv2").innerText = ""
            }
            // 给按文本框绑定失焦事件
            document.getElementById("myInput").onblur = function (){
                // 提示信息
                document.getElementById("myDiv2").innerText = "请点击验证查看结果"
            }
        }
    </script>

    <div id="myDiv1">
        <!--文本框-->
        <input type="text" id="myInput">
        <!--按钮-->
        <input type="button" value="点击验证" id="myButton">
    </div>

    <div id="myDiv2"></div>
</body>
</html>
```
#### <font class="text-color-7" color="#03a9f4">重写 trim 函数例子</font>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>test</title>
    <style type="text/css">
        #myDiv1{
            background-color: lightblue;
            border: 2px black solid;
        }
        #myDiv2{
            background-color: silver;
            border: 2px black solid;
        }
    </style>
</head>
<body>
<script>
        window.onload = function(){
            // 重写 String 的 trim 函数
            String.prototype.trim = function(){
                return this.replace(/^\s+/, "").replace(/\s+$/, "")
            }

            // 测试
            document.getElementById("myButton").onclick = function(){
                let msg = document.getElementById("myInput").value
                msg = msg.trim()
                document.getElementById("myDiv2").innerText = ">"+ msg +"<"
            }
        }
</script>

<div id="myDiv1">
    <!--文本框-->
    <input type="text" id="myInput">
    <!--按钮-->
    <input type="button" value="去除前后空白" id="myButton">
</div>

<div id="myDiv2"></div>
</body>
</html>
```
## <font class="text-color-121" color="#ffeb3b">其他</font>

### <font class="text-color-141" color="#ff9800">自定义日期格式</font>
* 可以使用JavaScript中的Date对象来获取年月日信息，并使用字符串拼接的方式输出。下面是一个示例代码，可以获取当前时间的年月日，并以“YYYY-MM-DD”的格式输出：

* 示例
```javascript
var today = new Date();
var year = today.getFullYear();
var month = today.getMonth() + 1;
var day = today.getDate();

// 月份和日期不足两位数时，在前面补0
month = month < 10 ? '0' + month : month;
day = day < 10 ? '0' + day : day;

var dateStr = year + '-' + month + '-' + day;
console.log(dateStr); // 输出格式为"YYYY-MM-DD"的日期字符串
```
### <font class="text-color-141" color="#ff9800">网页时钟</font>
* 使用 window 对象的两个方法：<a href="https://www.runoob.com/jsref/obj-window.html">window 对象文档</a>

* `setInterval()` 是 JavaScript 中的一个函数，可以定期执行一个函数或一段代码。它接受两个参数：要执行的函数或代码块以及执行的时间间隔（以毫秒为单位）。使用 `setInterval()` 可以在指定的时间间隔内重复执行指定的函数或代码块。

* `clearInterval()` 是 JavaScript 的一个函数，用于停止使用 `setInterval()` 函数创建的定时器。当使用 `setInterval()` 函数创建了一个定时器之后，可以使用 `clearInterval()` 函数停止该定时器的运行。
```javascript
clearInterval(intervalID)
// 其中 `intervalID` 是一个由 `setInterval()` 函数返回的 ID 值，用于指定要停止的定时器。
```

* 时钟
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Login Page</title>
</head>
<body>
    <script>
        var timerId; // 用于存储定时器ID

        // 开始计时器并显示时间
        function startTimer() {
            timerId = setInterval(function() {
                var now = new Date();
                var timeElement = document.getElementById("time");
                timeElement.innerText = now.toLocaleTimeString();
            }, 1000);
        }

        // 停止计时器并隐藏时间
        function stopTimer() {
            clearInterval(timerId);
            var timeElement = document.getElementById("time");
            timeElement.style.display = "none";
        }
    </script>

    <button onclick="startTimer()">开始显示时间</button>
    <button onclick="stopTimer()">停止显示时间</button>
    <p id="time"></p>
</body>
</html>
```
## <font class="text-color-121" color="#ffeb3b">JSON</font>
* JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，它基于JavaScript语言的一个子集。JSON格式的数据可以被JavaScript轻松解析，也可以被大多数现代编程语言读取和写入。JSON格式的数据一般使用一些常见的数据结构，如对象、数组、字符串、数字、布尔值和 null。

* JSON的主要特点如下：

1. 易于阅读和编写：JSON格式的数据使用简单的文本格式，易于人类阅读和编写，并且可以通过JavaScript的内置函数进行解析和序列化。
  
2. 轻量级：相比其他数据交换格式如XML，JSON格式的数据具有较小的数据体积，这使得它成为移动设备和低带宽网络环境下的首选数据格式。
  
3. 语言无关性：JSON格式的数据可以被几乎所有编程语言读取和写入，这使得它成为跨平台应用程序之间数据交换的标准格式。
  
4. 易于使用：JSON格式的数据可以被JavaScript内置的JSON对象快速解析和序列化，并且可以被许多开源的JSON库和API支持。

### <font class="text-color-141" color="#ff9800">JSON对象</font>
* 使用 JSON 字面量创建 JSON 对象：
	JSON 字面量是使用 JavaScript 对象语法创建的 JSON 对象。JSON 字面量以大括号 `{}` 开头和结尾，并包含一系列用逗号分隔的键值对。
```javascript
var myObj = {
  "name": "John",
  "age": 30,
  "city": "New York"
};
```
* 访问 JSON 对象的元素（可以使用点号（.）或方括号（[]）符号。）
```javascript
console.log(myObj.name); // 输出 "John"
console.log(myObj["age"]); // 输出 30
```
* 复杂一点的 JSON 对象例子
```javascript
{
  "name": "John Doe",
  "age": 30,
  "address": { // JSON 对象
    "street": "123 Main St",
    "city": "Anytown",
    "state": "CA",
    "zip": "12345"
  },
  "phoneNumbers": [  // JSON 数组
    {
      "type": "home",
      "number": "555-555-1212"
    },
    {
      "type": "work",
      "number": "555-555-2121"
    }
  ]
}
```
#### <font class="text-color-7" color="#03a9f4">JSON数组</font>
* JSON数组可以通过在方括号中添加逗号分隔的JSON对象或JSON值来创建。
```javascript
var jsonArray = [
  { "name": "John", "age": 30, "city": "New York" },
  { "name": "Mary", "age": 25, "city": "Los Angeles" },
  { "name": "Bob", "age": 40, "city": "San Francisco" }
];
```
### <font class="text-color-15" color="#ff9800">eval()</font>
* 可以使用 `eval()` 函数将 JSON 格式字符串转换为 JSON 对象。例如：
```javascript
var jsonStr = '{"name": "John", "age": 30, "city": "New York"}';
var jsonObj = eval('(' + jsonStr + ')');
console.log(jsonObj.name);  // 输出 "John"
```
* 在使用 `eval()` 函数解析 JSON 格式字符串时，需要在字符串前后加上圆括号，这是因为 JavaScript 在解析圆括号时会把它们当作一个代码块的开始和结束，如果不加圆括号，解析时会出错。另外，`eval()` 函数存在一些安全风险，如果被传递的字符串中包含恶意代码，会对系统造成危害，因此不推荐在生产环境中使用。

### <font class="text-color-15" color="#ff9800">用表格展示JSON数组例子</font>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Login Page</title>
</head>
<body>
    <script>
        let emp = {
            total : 5,
            empSal : [
                {eno : "001", ename : "Smith", esal : 5600},
                {eno : "002", ename : "John", esal : 4500},
                {eno : "003", ename : "Sarah", esal : 6500},
                {eno : "004", ename : "David", esal : 7200},
                {eno : "005", ename : "Linda", esal : 5200}
            ]
        }

        window.onload = function(){
            document.getElementById("tableButton").addEventListener("click", function(){
                let html = ""
                let empSal = emp.empSal
                for (let i = 0; i < emp.total; i++) {
                    html += "<tr>"
                    html += "<td>"+ empSal[i].eno +"</td>"
                    html += "<td>"+ empSal[i].ename +"</td>"
                    html += "<td>"+ empSal[i].esal +"</td>"
                    html += "<tr>"
                }
                document.getElementById("tableBody").innerHTML = html
                document.getElementById("totalSpan").innerText = "总记录条数" + emp.total
            })
        }
    </script>

    <button id="tableButton">显示员工薪资表格</button>

    <table border="1" width="50%" align="center" style="text-align:center">
        <thead>
        <tr>
            <th>员工编号</th>
            <th>员工姓名</th>
            <th>员工薪资</th>
        </tr>
        </thead>
        <tbody id="tableBody"></tbody>
    </table>

    <div style="text-align: center;">
    <span id="totalSpan"></span>
    </div>
</body>
</html>
```



