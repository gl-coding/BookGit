# 第2节：JavaScript

# JavaScript 运行

## 运行

JavaScript 代码的执行方式跟 [CSS](https://www.jmjc.tech/less/15) 一样，同样的嵌套在 [HTML](https://www.jmjc.tech/less/1)代码中，同样的有三种方法。

```js
<html>
<head>

 <script src="path_to/file.js" type="text/javascript" /> <!-- 1. JavaScript 文件载入 -->

 <script type="text/css"> <!-- 2. <script> 标签载入  -->
  alert('Hello JavaScript ~')
 </script>

</head>

<body>

 <em onclick="alert(' Hello JavaScript ~ ')"> JMJC.TECH </em> <!-- 3. 属性载入 -->

</body>
</html>
```

------

## 调试

浏览器一般都会自带一个前端调试工具，以 Chrome 为例，按 `F12` 键 或者右键网页`查看元素`可以打开。

```js
// console.log 是一个打印变量的函数，结果显示在调试工具的控制台

console.log('Hello ～')
```

------

## 注释

`.js` 文件的代码注释。

```js
// alert('单行注释')

/*
 function() {
  alert('多行注释')
 }
 ... 
*/
```

------

## 分号

JavaScript 代码的结尾是否使用分号 `;` 长期分为两派并且看对方互相不顺眼，双方都非常有理由也没有妥协下来，所以具体加不加分号就看团队和个人习惯。

# JavaScript 数字

## Number 类型

JavaScript 的 number 类型具体又分为四类 `整数`、`浮点数`、`NaN` 和 `Infinity`。

------

```js
整数
console.log(1)
console.log(-1)
```

------

```js
浮点数
console.log(1.0)
```

------

`NaN`*（代表不是数字）*

```js
/* NaN 类型 */
console.log(0 / 0) // NaN
Number('a') // NaN

/* 判断对象是否是 NaN */
isNaN(NaN) // true
isNaN('a') // true
isNaN(1) // false

/* 这是一个坑 | 想要判断一个 NaN 对象，尽量使用 isNaN 函数 */
NaN != NaN // true
```

------

`Infinity`*（无穷大）*

```js
console.log(1/0) // ∞
```

------

## typeof

```js
类型检测
typeof 1 // 'number'
typeof 1.0 // 'number'
typeof NaN // 'number'
typeof Infinity // 'number'
```

------

## 数学运算

```js
// + 加 | - 减 | * 乘 | / 除

// 取余
console.log(10%3) // 1

// 10的倍数
console.log(2e3) // 2 * 1000

// 次方
console.log(2**3) // 2 * 2 * 2
```

------

## 数字转换

```js
// 字符串转数字
Number('1') // 1
Number('1.1') // 1.1

// 浮点数转整数
parseInt(1.1) // 1
```

## String 类型

JavaScript 字符串的表示方法是 。

```js
typeof '单引号' // 'string'
typeof "双引号" // string
```

------

## 索引

字符串也是`序列`，所以可以通过序列的排序编号进行取值。

```js
var str ="abcdef"

/*
a | 0
b | 1
c | 2
d | 3
e | 4
f | 5
*/

console.log(str[0]) // 'a'
console.log(str[4]) // 'e'
```

------

## 不可变性质

字符串这种序列跟列表结构是有区别的，它是不可以修改和排序的。

```js
var letter = 'abc'

letter[0] = 'f'

console.log(letter) // abc
```

------

## 字符转译

JavaScript 中的字符转译。

```js
// 转译 ' 单引号
console.log('\'') // '

// 转译 ' 单引号
console.log("\"") // "

// 转译 ascii
console.log('\x41') // A

// 转译 unicode
console.log('\u0041') // A

// 换行 \n
console.log("\n")

// windows 操作系统换行的转译是 \r\n
console.log("\r\n")

// 制表符 | tab键
console.log("\t")
```

------

## 多行字符

\```` 符号可以表示多行字符串。

```js
var str = `a
b
c
...
`

console.log(a)
/*
a
b
c
...
*/
```

------

## 字符拼接

```js
console.log('a' + 'b') // 'ab'
```

------

## 格式化

在字符串中插入变量，也叫格式化字符串。在 ES6 标准之后支持 `` ${var} `` 这种格式化语法。

```js
var str name = 'Ada'

// 传统格式化方法
console.log("She's name is" + name + '.') // She's name is Ada.

// 注意必须是 `` 符号
console.log(`She's name is ${name}.`) // She's name is Ada.
```

------

## 弱类型

在`强类型`的语言中，例如 `Python`，一个数字类型和一个字符串类型相加，会提示错误。而像 `JavaScript` 这种弱类型的语言，会通过 `隐式转换` 组合两个不同类型的数据。

```js
console.log(1 + '1') // 11，被转换成了字符串
```

------

## URL 编码

对URL中特殊字符的转译。

```js
// 编码
encodeURI('https://www.jmjc.tech/?name=简明教程') // "https://www.jmjc.tech/?name=%E7%AE%80%E6%98%8E%E6%95%99%E7%A8%8B"

// 解码
decodeURI("https://www.jmjc.tech/?name=%E7%AE%80%E6%98%8E%E6%95%99%E7%A8%8B") // 'https://www.jmjc.tech/?name=简明教程'
```

------

## 字符串方法

常用的一些字符串操作方法。

```js
''.length // 0 | 获取长度

'abc'.toUpperCase() // 'ABC' | 大写

'ABC'.toLowerCase() // 'abc' | 小写

'abc'.indexOf('d') // 字符首次索引位置，不存在返回 -1

'abc'.substr(0, 2) // 'bc' | 切片，从第 0 位开始 “获取” 2 位

'fly.jpg'.endsWith('.jpg') // true | 判断结尾字符

'a'.replace('a','b') // 'b' | 替换

'a,b,c'.split(',') // [a, b ,c] | 裁剪
```

## Array 类型

数组是可变有序的集合，可以存储任意的数据类型，JavaScript 的数组表示符号是 `[]`。

```js
[1, 2, 3.14, 'Hello', null, true, [], {}] // 数组结构

// 注意：用 typeof 验证数组的类型返回的是 'object' ，合理的情况返回的应该 'array'，这也是 JavaScript 的坑之一，详细的 “类型检测” 请查看后面相关章节
typeof [] // "object"
```

------

## 操作数组

```js
// 创建
var arr = [1,2,3]

// 取值
console.log(arr[1]) // 2

// 赋值
arr[0] = 'a'
console.log(arr) // ['a',2,3]
```

------

## 数组方法

常用的一些数组操作方法。

```js
[].length  // 0 | 长度

[1,2,3].indexOf(2) // 元素首次出现的索引位置，不存在返回 -1

['a','b','c'].slice(0,2) // 'bc' | 切片，从第 0 位到第 2 位

[1,3,2].sort() // [1,2,3] | 排序

[1,3,2].sort() // [2,3,1] | 反转

/* push 添加元素到末尾，并返回最新长度 */
var arr = [1,2]
console.log(arr.push(3)) // 3
console.log(arr) // [1,2,3]

/* pop 弹出数组最后的元素 */
var arr = [1,2,3]
console.log(arr.pop()) // 3
console.log(arr) // [1,2]

/* unshirt 添加元素到开头，并且返回最新长度 | 相反的 push */
/* shirt 弹出数组第一个元素 | 相反的 pop */

/* concat 合并 */
var a = [1,2]
var b = ['a', 'b']
var c = a.concat(b)
console.log(c) // [1, 2, "a", "b"]

/* splice 替换 */
var arr = [1,2,3]
console.log(arr.splice(1,2,'a')) // 从 1 位开始替换掉 2 位 | 并且返回被替换的值 [2,3]
console.log(arr) // [1,'a']

/* splice 删除 */
var arr = [1,2,3]
console.log(arr.splice(1,2)) // 从 1 位开始删除掉 2 位 | 并且返回被删除的值 [2,3]
console.log(arr) // [1]
```

## Object 类型

JavaScript 的对象类似于其他语言的哈希结构，是一种无序的 `key => value` 集合，用 `{}` 符号表示。

```js
 // 创建 | Object 的 key 必须是 “字符串” 或者 “数字” 这种 “不可变性质” 的类型，并且不能重复，value 可以是任意的
var person = {
 name: 'Ada',
 age: 19
}

// 取值
console.log(person.name) // 'Ada'
console.log(person['name']) // 同上

// 赋值
person.birth = 1896

// 删除
delete person.birth
```

------

## 属性检测

```js
'Ada' in {'Ada': 1} // true | 验证属性是否存在
```

------

## 对象方法

```js
Object.keys({a: 1, b: 2}) // [a, b] | 获取 key
Object.values({a: 1, b: 2}) // [1, 2] | 获取 value
Object.assign({a:1}, {b:2}) // {a:1, b:2} | 合并，重复的 key 会被覆盖
```

------

## 是否为空

判断一个 `{}` 是否是空的。

```js
{} === {} // false | 就像 NaN !== NaN 一样，两个 {} 也不相等
{}.length // 报错 | length 是获取一个 “序列” 的长度，对象并不是序列，所以没有 length 方法

// 需要先把 {} 转换成 []，才能验证是否为空
Object.keys({}).length // 0 
```

------

由于 JavaScript 的 object 类型它既是一种哈希数据结构，又是我们面向对象编程传统意义上的 “对象”。为了不混淆概念，ES6标准新推出了一种哈希结构 [Map](https://www.jmjc.tech/less/41) 和 集合数结构 [Set](https://www.jmjc.tech/less/42)。

## Map 类型

ES6 标准之后的哈希结构，针对 object 类型的修补。

```js
//  创建
m = new Map([[1,'a'], [2,'b']])
console.log(m) // {1 => "a", 2 => "b"}

// 取值
m.get(1) // 'a'

// 赋值
m.set(3, 'c')

// 删除
m.delete(3) // true or false

// 验证 Key 是否存在
m.has(3) // true or false

// 长度
m.size // 2

// 获取 Key | 返回一个可迭代对象，具体查看迭代相关章节
m.keys() // MapIterator {1, 2}

// 获取 Value
m.values() // MapIterator {'a', 'b'}
```

## Set 类型

`Set` 是只能存 `Key` 的 `Map`，所以它继承了哈希中 Key 的所有性质，只能存放不可变类型，也不能重复。

```js
// 创建
s = new Set([1,'a'])

// 新增
s.add(3)

// 删除
s.delete(3)

// 判断
s.has(3)

// set 取值方法，只能迭代
```



## null 类型

`null` 代表什么也没有。

```js
/* 0、空字符串、空数组、空对象，都不是 null，虽然他们没有值但是有具像，而 null 代表的是 “什么都没有” */
null != 0 // true
null != '' // true
null != [] // true
null != {} // true

null === null // true

/* JavaScript 的 null 的类型也是 'object' */
typeof null // 'object'
```



## undefined 类型

`undefined` 代表值不存在。

```js
// 变量不存在
typeof v // 'undefined' | “此处有坑” typeof 检测变量返回的是 'undefined' 而不是 undefined，前者是字符串类型，后者是 undefined 类型

// 索引不存在
[][0] // undefined
 
// 没有传递参数
(function (a) {
    console.log(a) // undefined 
})();

// 函数没有返回值
console.log(function () {} ()); // undefined
```



## 类型检测

JavaScript 各种类型的检测方法。

```js
typeof 123 // 'number'
typeof 'abc' // 'string'
typeof undefined // 'undefined'
typeof true // 'boolean'
typeof Math.abs // 'functuon'

null === null // true

[] instanceof Array // true
{} instanceof Object // true
new Map instanceof Map // true
new Set instanceof Set // true 
```

------

## 相等与恒等

相等判断也是 JavaScript 的坑之一。

```js
// 相等 | 值相等
'1' == 1 // true

// 恒等 | 值并且类型相等
'1' === 1 // false

// 这看起来没什么问题，但是 undefined == null == '' == 0 == [] == {} == false // 居然等于 true
// 所以，在 JavaScript 中尽量使用 === 恒等进行判断。
```



## 包装对象

JavaScript 又一坑之一。

```js
// 创建一个数字
var num = 123
var num = Number(123)
var num = new Number(123)

/* 
这三种创建方法最后 num 的值都是 123，但是他们的类型却是不相等的
123 === Number(123) !== new Number(123) // true 
*/

/* 
数组版： Array([1]) !== [1] !== new Array([1]) 
...
*/

// 所在必须记住在声明类型的时候，要抛弃这种坑爹的 new Number(123) 的 “包装对象” 
```

# JavaScript 条件判断

## 逻辑判断

逻辑运算中的条件判断。

```js
1 === 1 // true | 相等

1!== 1 // false | 不等

1 < 1 // false | 小于 

1 > 1 // false | 大于 

1 <= 1 // true | 小于或等于

1 >= 1 // true | 大于或等于

1 == 1 && 1 == 2 // false | 与运算、两边的条件符合成立

1 == 1 || 1 == 2 // true | 或运算、一边条件符合即成立
```

------

## if 语句

if 条件语句的几种形态。

```js
// if
if (true) {
 // 执行
}

// if else
if (1>2) {

} else {
 // 执行
}

// else if
if (1>2) {

} else if (1<2) {
 // 执行
} else {

}
```

------

## switch 语句

if 之外的另一种条件判断语句。

```js
var n = 1

switch(n) {
case 1:
  // n = 1 执行
  break;
case 2:
  // n = 2 执行
  break;
default:
  // n 既不等于 1 也不等于 2 执行
}
```

# JavaScript 循环

## for 循环

```js
实例
for (var i=0; i<5; i++) { // 参数（初始值；条件；每循环一次修改初始值、当初始值不在满足条件，循环就被终止）

 console.log(i)

 // 0
 // 1
 // 2
 // 3
 // 4

}
```

------

## while 循环

```js
实例
var 1 = 0

while (i<5) { 
 
console.log(i)

 // 0
 // 1
 // 2
 // 3
 // 4

 i++ // 每循环一次 i + 1，当 i = 5 不在满足条件循环结束

}
```

------

## continue

跳过当前循环。

```js
for (var i=0; i<5; i++) {

 if (i === 2) { // 当 i = 2 时，跳过当前循环
  continue
 }

 console.log(i)

 // 0
 // 1
 // 3
 // 4

}
```

------

## break

退出整个循环。

```js
for (var i=0; i<5; i++) {

 if (i === 2) { // 当 i = 2 时，终止循环
  break
 }

 console.log(i)

 // 0
 // 1

}
```



# JavaScript 函数

## function

JavaScript 函数的基本语法。

```js
// 定义函数
function now() {
 console.log(new Date().toLocaleString()) // 输出当前时间
}

console.log(now) // [Function: f]
console.log(typeof now) // 'function'

// 执行函数
now() // "2018/8/29 下午1:15:23"
```

------

## return

函数的返回值。

```js
function f () {
 return 0 // 返回 | 没有设置返回值默认返回 undefined
 console.log('...') // return 代表函数结束，之后的代码不会被执行
}

var n = f()
console.log(n) // 0
```

## 参数

JavaScript 函数的参数。

```js
function f(a, b, c) { // 参数可以声明多个并且支持是任意类型
 console.log(a)
 console.log(b)
 console.log(c)
}

f(1, 'a')
// 1
// 'a'
// 未传递参数的值等于 'undefined'  
```

------

## 默认参数

参数的初始值。

```js
function f(num = 0) {
 console.log(num)
}

f() // 0 | 如果不传参，num 的默认值是 0

f(1) // 1
```

------

## arguments

参数对象。

```js
(function(){
 console.log(arguments) // {0:'a',1:'b',2:'c'} | 获取所有的参数
 console.log(arguments.callee) // [Function] | 获取当前函数对象
 
 // arguments.callee() 可以看成是匿名函数的递归操作

})('a','b','c')
```

------

## rest

参数打包。

```js
(function(a,b,...rest){
 console.log(a,b,rest) // 1 2 [3,4] | rest 是一个数组，用于保存多于的参数
})(1,2,3,4);
```



## 匿名函数

匿名函数是`函数式编程`一个重要的特性，它让函数与函数之间变得很灵活。

```js
 // 匿名函数
(function() {}) 

// 匿名函数赋给一个变量，就等同于 function f() { ... }
var f = (function () {})  

// 匿名函数虽然没有名字，但可以 “自执行”
(function() {
 console.log(1) // 1
})()
```

------

## 函数参数

函数作为参数传递。

```js
function f () { 
 console.log('f') 
}

(function(f) {
 f() // 'f'
})(f)
```

------

## 返回函数

函数作为返回值。

```js
var f = (function() {
 return (function() { console.log('f') }) // 返回一个函数
})()

// 执行返回的函数
f() // f
```



## 箭头函数

箭头函数是 `ES6标准` 新的函数语法，可以看出是匿名函数的简写形式。

```js
// 箭头函数
var f = ((x) => {
 return x + x
})

// 这两种方法是等价的
var f = function(x) {
 return x + x
}

f(3) // 9

/*
 当箭头函数只有一行的时候，{} 和 return 可以被省略
 var f = x => x * x  // 函数的功能同上
*/
```



## 递归

在函数的内部执行函数本身称为递归，递归的本质是一个`循环`。

```js
function f() {
 console.log(1)
 f() // 递归
}

f() // 没有条件阻止，递归就是一个死循环
// 1
// 1
// ...
```

------

## 递减

设置一个条件。

```js
function minus(n) {
 if (n === 0) return // 条件，到 0 退出
 console.log(n)
 minus(n - 1) // 递归 - 1
}

minus(5)
// 5
// 4
// 3
// 2
// 1
```

# JavaScript 闭包

## 内部变量

函数内部的变量，在函数外部是无法获取并且修改的。

```js
function f() {
 var n = 1
 n = n + 1 // 我们打算让每执行一次，n+1
 return n
}

f() // 2
f() // 2
f() // 2

// 每次执行函数，变量都被重新设置，并没有实现我们要的效果
```

------

## 闭包

闭包就是在函数的内部，在构建一个子函数，去影响函数的值，从而达到修改函数内部变量的效果。

```js
function f() {
 var n = 0
 return (function() {
   console.log(n++) // 子函数，每次修改父函数的 n + 1，并且通过父函数返回到外部
 })
}

add = f()
add() // 0
add() // 1
add() // 2
```

# JavaScript 生成器

## 生成器

生成器是一种`惰性的序列`，它支持一边读取数据，一边生成数据，如果数据比较大时，这种机制能节省很多内容空间。JavaScript 在 ES6 标准中也新增了对生成器的支持。

```js
/* 
 生成器的构造是用函数来包装，但是我们应该把下例看成是一个 [1,2,3,4,5] 的序列，而不是一个函数
*/

function* f() {
 for (let i=0; i<5; i++){
  yield i // 返回并记录函数状态
 }
}

var f = f()

console.log(f.next()) // { value: 0, done: false }
console.log(f.next()) // { value: 1, done: false }
console.log(f.next()) // { value: 2, done: false }
console.log(f.next()) // { value: 3, done: false }
console.log(f.next()) // { value: 4, done: false }
console.log(f.next()) // { value: undefined, done: true }

/*
  每调用一次 next，就执行一次 yield | 依靠这种需要才生产的工作机制，大大的节省资源
*/
```



## 作用域

作用域是代码的影响范围，函数的内部有属于自己的作用域。

```js
var n = 1

console.log(n) // 1

;(function() {
 n = 2
})()

console.log(n) // 1 | 没有被函数影响
```

------

## 全局变量

所有作用域下都能共享都变量。

```js
/*
var n = 1 // 局部变量
n = 1 // 全局变量 

浏览器中的 JavaScript，当变量没有指定前缀就是全局变量 
因为，n = 1 和 window.n = 1 相等，window 在浏览器中是全局对象
而 Node.js 全局变量和一般语言一样，用的是 global 语法
*/

n = 1

console.log(n) // 1

;(function() {
 n = 2
})()

console.log(n) // 2 | 成功改变了 n 的值
```

------

## let

ES6 新增的变量关键词，和 `var` 最大的区别是 `let` 具备`块级作用域`。

```js
// 每一个 {} 就是一段代码块

// let
for (let i=0; i<5; i++){
 // ...
}

console.log(i) // 读取不到，而如果使用的是 var 这里可以就读取得到
```

------

## const

ES6 新增的`常量`关键字，和 let 一样具备块级作用域。

```js
const page = 10

page = 5 // 常量，定义量就不能修改，否则报错
```

------

## strict

```js
严格模式
'use strict' // 文件开头声明，启用严格模式

/*
 严格模式会对不规范的代码进行报错，建议开启，养成代码规范的好习惯！
*/
```



## this

当前作用域下的对象。

```js
/* 例 1. */
var Obj = {
 n:1,
 f:function(){
  return this.n // f 函数 在 Obj 的作用域下执行，所以 this 代表了 Obj，this.n = Obj.n
 }
}

n = Obj.f()
console.log(n)


/* 例 2. */
var Obj = {
 n:1,
 f:function(){ return (function() {return this.n})() } // 嵌套多层函数会导致 this 失效
}

n = Obj.f()
console.log(n) // undefined


/* 例 3. */
var Obj = {
 n:1,
 f:function(){ return (()=>this.n)() } // 箭头函数修复了嵌套多层函 this 失效的问题
}

n = Obj.f()
console.log(n) // 1
```

# JavaScript 迭代

## 字符串

迭代是对数据的 `遍历`，下面是 JavaScript 中字符串的迭代方法。

```js
// for of
for (let v of 'abc'){
    console.log(v)
}

// a
// b
// c
```

------

## 数组

数组的迭代方法。

```js
/* for of */
for (let v of [1,2,3]){
    console.log(v) // 1 2 3
}

/* forEach */
['a','b','c'].forEach(function(element,index,array){
    console.log(element) // 当前元素
    console.log(index) // 当前索引
    console.log(array) // 迭代对象
})

// 'a'
// 0
//[ 1, 2, 3 ]

// 'b'
// 1
//[ 1, 2, 3 ]

// 'b'
// 2
// [ 1, 2, 3 ]
```

------

## 对象

对象的迭代方法，需要注意对象的迭代方式 `for in`，而不是 `for of`。

```js
// for in
var obj = {a: 1, b: 2}
for (let o in obj) {
 console.log(o)
 console.log(obj[o])
}

// 'a'
// 1

// 'b'
// 2

/*
 也可以把对象转换成数组在迭代 
 Object.keys({a: 1, b: 2}) // [a, b]
 Object.values({a: 1, b: 2}) // [1, 2]
*/
```

------

## Map

map 的迭代方法。

```js
m = new Map([[1,'a', 2, 'b']])

// forEach
m.forEach(function(key, value, map) {
 // 'a'
 // 1
 // new Map([[1,'a', 2, 'b']])
 // ...
}) 

// for of
for (let m_k of m.keys()){} // 1,2
for (let m_v of m.values()){} // a,b
```

------

## Set

set 的迭代方法。

```js
for (let s of new Set([1,2])){
    // 1,2
}
```

# JavaScript Date

## 时间对象

`Date` 是 JavaScript 的时间对象，关于时间的工作，都是由这个对象负责。

```js
new Date() instanceof Date // true

// 默认返回当前时间的时间对象
new Date()

// 自定义时间
new Date('2017-5-23 00:00:00') // 通过 “标准时间格式” 指定
new Date(1502587638950) // 通过 “时间戳” 指定
```

------

## 格式化

把时间对象转换成日期格式。

```js
new Date().getFullYear() // 2018 | 年
new Date().getMonth() // 9 | 月 （0 ～ 11 代表 1 - 12 月份）
new Date().getDate() // 21 | 日
new Date().getDay() // 5 | 星期几
new Date().getHours() // 14 | 时
new Date().getMinutes() // 20 | 分
new Date().getSeconds()  // 14 | 秒
new Date().getMilliseconds() // 930 | 毫秒
new Date().getTime() // 1537510914079 | 时间戳
```

------

## 时间运算

编程中的时间运算，通常都是通过时间戳来加减，之后在把时间戳转换成 `标准时间格式`。

```js
// 得到一个7天后的时间对象 

new Date(new Date().getTime() + (7 * 24 * 60 * 60 * 1000)) // + 7天
```

------

## 标准时间格式

时间的显示形式，有一个约定俗成的标准 `2018-9-21 14:32:18`，日常我们所见的，都是这种格式。格式的统一方便在不同语言中处理，大部分的现代高级语言，内置的时间处理工具，都能轻易的把时间对象格式成这种格式，但是 JavaScript 并没有这种能力，它转换出来的时间格式不标准。

```js
new Date().toLocaleDateString() // 2018/9/21
new Date().toLocaleString() // "2018/9/21 下午2:38:22"

/*
 浏览器中的 JavaScript 和 服务端的 Node.js 转换出来的格式有略微的差别，但是两者都不标准
 如果想得到一个 “标准的时间格式”，可以通过第二段 “格式化” 的内容，年/月/日/时/分/秒，自己逐个的拼装
 moment 是一个 JavaScript 的第三方时间处理工具，它能方便的得到我们想要的 | moment().format('YYYY-MM-DD HH:mm:ss')
*/
```



## 数学对象

`Math` 是 JavaScript 的一个内置对象，提供了一些常用的数学方法。

```js
Math.abs() // 绝对值
Math.random() // 0 ~1 随机数
Math.max(1, 2) // 2 | 最大值
Math.min(1, 2) // 1 | 最小值
Math.ceil(25.1) // 26 | 向上舍入
Math.floor(25.1) // 25 | 向下舍入
Math.round(25.1) // 25 | 四舍五入
```



## JSON 格式

`JSON` 格式的标准定义就是来源于 JavaScript 的 `{}`，两者几乎是一样的，只是 JSON 稍微严格。

```js
/*
 JSON 的本质是字符串形式的 object 类型 '{...}' | 因为只有 “序列化” 成字符串，才能通过网络编码传输
 typeof _JSON "string"
*/

var _JSON = '{
 "name": "jobs",
 "age": 17, 
 "like": ["strawberry", "bread"],  
 "parents": {"mon": "Lily", "dad": "mark"}, 
 "married": false,
 "money": null
}'

/*
 严格
 */
var obj = {
 name: 'job', // object 类型的 key 可以不带 引号、单引号、双引号，而 JSON 统一规定，字符串必须是 “双引号”
 'age': 17,
 "like": [...]
}
```

------

## 编码

把 JavaScript 对象编码成 `JSON`。

```js
var obj = {
    name: 'eva',
    age: 3
}

// 正常格式化
JSON.stringify(obj) // '{"name":"eva","age":3}'

// 友好显示
JSON.stringify(obj,null)

// 过滤 
JSON.stringify(obj,['name']) // '{"name": "eva"}' |  只保留 name

// 定制
JSON.stringify(obj,function (key, value) {
    if (key === 'name'){
        return value + ' cai'
    }
    return value
})

'{"name":"eva cai","age":3}'
```

------

## 解码

把 `JSON` 解码成 JavaScript 对象。

```js
JSON.parse('{"name":"eva","age":3}') // {name: "eva", age: 3}

// 定制
JSON.parse({}, function (key, value) { ... })  // 同上
```

# JavaScript 异步编程

## 异步

JavaScript 是一门 `单线程` 并且依靠 `异步` 机制实现多任务的语言，跟大多数默认是同步编程的语言不同的是，JavaScript 的代码不是顺序执行的，这样设计的目的是出于性能的需要，但这个特性可能会给新手带来困扰，关于异步编程的思想，可以参考 - [异步编程](https://www.jmjc.tech/tutorial/python/47)。

## sleep

sleep 是 python 中的一个睡眠函数。

```js
import time

print(1)
time.sleep(1) # 暂停 1 秒
print(2)

# 返回结果
1
2
```

------

## setTimeout

setTimeout 是 JavaScript 中的 `“sleep”`，但由于 python 是同步的，javaScript 是异步的，所以它们两者对暂停有不同的理解。

```js
console.log('a')

// 暂停一秒 （阻塞）
setTimeout(function (){
    console.log('b')
}, 1000)

console.log('c')

// 返回结果
'a'
'c'
'b'
```

异步的代码，对待所有的 `阻塞`，都会暂时的先跳过，等待阻塞完毕之后在返回执行，所以造成了我们的结果返回的是 `a/c/b`。因为只有一个线程，如果暂停了，那么整个程序也就卡死了。

## setInterval

```js
循环阻塞
/*
 for setTimeout
*/

// 我们想每次循环暂停1秒，并且输出当前的循环值。

var i=1

while (true) {
 setTimeout(function() {
  console.log(i)
 }, 1000)

 if (i=5) break
 i++
}

// 返回结果 | 5
// 所以 setTimeout 显示不适用于上面场景，在它阻塞1秒的这段时间，while已经跑了5次循环，累计到了5。


/*
 setInterval
*/

var i=1
var int = setInterval(function f() {
 console.log(i)

 if (i===10) clearInterval(int) // 停止
 i++
}, 1000)

// 返回结果 (1,2,3,4,5,6,7,8,9,10)
// setInterval 就是用于解决上面这种应用场景
```

## callback

`回调` 是 JavaScript 异步编程的设计模式，这种模式延续了很多年，直到 `Node.js` 的出现，把 JavaScript 推向了服务端领域，处理更复杂的业务场景，才有了之后的 `Promise`、`async await`，我们前面演示的异步代码，实际都是通过 `回调执行`。

```js
// 回调函数
function f() {
 console.log('callback')
}

setTimeout(f, 1000) // 阻塞 | 假设它在做一个 “网络请求”

console.log('...')
```

回调的实现方式也很简单，就是通过传入一个`回调函数`，只是，当业务复杂时，一层又一层的回调，在回调函数里在嵌套回调函数，会显得代码混乱不够优雅，甚至得名 `地狱回调`。

## Promise

异步模型的最高境界就是 `同步`，或者说，代码的执行流程是异步的，而我们写代码是思维是同步的，`Promise` 是通往这条道路的一次探索。

```js
var p = new Promise(function(r) {
 setTimeout(function() {
  r(1) // 返回，之后通过 p.then 获取
 }, 1000)
})

// 在这个区域里面，就能写出同步代码，本来我们需要通过一次一次回调嵌套的东西，通过 Promise 的封装能够实现了同步执行
p.then(function(r) {
 console.log(r) // 同步的等待 setTimeout 1000
 console.log(2)
})

// 区域外的代码，依然是异步，不会阻塞了整个程序，照成卡死
console.log(0)

// 返回结果
0
1
2
```

## async await

`Promise` 实际上还不是完美的，有那么一点回调的影子， ES7 的 `async await`，又在 Promise 对象的基础上封装了一层，这个异步的解决方案目前也是大多编程语言的最新实现，几乎接近终极，python 也是支持的 - [python async await](https://www.jmjc.tech/tutorial/python/48) 。

```js
// 这个区域里面的代码，实现了真正的 “同步”
;(async function f() {
    console.log(1)

    // 等待一秒执行 | 以后的每个 “回调” 都是一个 “await” 
    r = await new Promise(function (res) {
        setTimeout(function () {
            res(3)
        }, 1000)
    })

    // 同步继续
    console.log(r)
    console.log(4)
})()

// 区域外依然是异步的
console.log(2)

// 1
// 2
// 3
// 4
```

# JavaScript 调试技巧

## console

在 JavaScript 的语言标准中, 是没有内置调试工具的. 由于 JS 是附属于浏览器中, 所有浏览器为它提供了一些调试的方法. `console` 就是其中的一个代表. 在不同的浏览器中 console 方法可能会出现略微的差别, 但是总体一致的.

------

## 输出

像 [Python](https://www.jmjc.tech/tutorial/python/1) 的 print, [PHP](https://www.jmjc.tech/less/162) 的 echo. JavaScript 往控制台打印输出使用的方法就是 `console.log`. 不同在于 console 比起 print、echo ... 要更加的强大, 就针对信息的输入而言, 它为我们定义了一些 `信息的级别`.

```js
console.log('正常输入')
console.info('普通级别')
console.warn('警告级别')
console.error('错误级别')

/*
 打印的信息都输出到浏览器的 “Developer Tools” 的 console 栏目
 拿 “Chrome 浏览器” 举例, console 栏目里有一个 Levels 选项可以帮助我们过滤打印的信息级别, 更方便我们定位错误
*/
```

------

## 断言

断言是一种常见的调试技巧, 它的用法就是我们`提前预判`程序的结果, 如果执行之后不符合我们的预判, 那么就报错.

```
function f(n) {
 console.assert(n !== 0, '零不能作为被除数') // 这里就是断言 | 提前预判
 return 10 / n
}

console.log(f(1)) // 10
console.log(f(2)) // 5
console.log(f(0)) // 报错 | Assertion failed: 零不能作为被除数
```

------

## 堆栈追踪

```
function f() { 
  console.trace() // 输出 f 函数的调用地址
}

f()
```

------

## 计时

这种方法是帮助我们计算一段代码的执行时间的.

```
console.time('time') // 开始
for (var i = 0; i < 1000; i++) {
  for (var j = 0; j < 1000; j++) {}
}
console.timeEnd('time') // 结束


// time: 5.11181640625ms (运行时间)
// ('time')  这个名字是这两组方法的标示, 名字可以是任意的, 相互对应为一组
```

------

## 计数

统计执行的次数.

```
for (var i = 0; i < 5; i++) {
    console.count('count')
  }

// count 1
// count 2
// count 3
// count 4
// count 5
```

------

## 对象信息

传入一个对象, 打印出这个对象的一些信息, 属性方法等... 非常有用.

```
console.dir(Object)
console.dir(Array)
...
```

------

## 格式化

信息显示到控制台的一些排版方式.

```
/* 
 分组显示
*/

console.group('一级')
 console.group('二级')
  
  console.log('error')

 console.groupEnd()
console.groupEnd()

/*
 表格显示
*/

console.table({
 name: '简明教程',
 url: 'jmjc.tech'
})
```

# JavaScript Ajax

## Ajax

`Ajax` 是一种不需要刷新网页，利于 `JavaScript` 提交 `HTTP请求` 然后改变网页显示状态的技术。

我们常见到的一个功能 `点击加载更多`。它的实现过程就是利于了 Ajax 从服务端获取到数据，然后用 [DOM](https://www.jmjc.tech/less/78) 技术把数据插入在文档中，整个过程我们的网页都不需要刷新，从而节约了很多请求资源。

JavaScript 操作 Ajax，依靠的是浏览器提供的 `XMLHttpRequest 对象`。

------

## XMLHttpRequest

```js
// 封装
var request = new XMLHttpRequest()

request.onreadystatechange = function () { // 回调
 if (request.readyState === 4) { // 成功
  if (request.status == 200) { 
   console.log(request.responseText) // 服务器响应内容
  } else {
   console.log(request.status)
  }
 }
}

// GET 请求
request.open('GET','https://www.jmjc.tech')
request.send()

// POST 请求
request.open('POST','https://www.jmjc.tech')
request.setRequestHeader("Content-Type","application/x-www-form-urlencoded")
request.send('key=value') // 参数
```

# JavaScript 跨域请求

## 同源策略

浏览器对 `XMLHttpRequest `对象的 HTTP 请求，是有范围限制的，这项规定被称为 `同源策略`。总共有 `3条` 限制。

`1. 域名相同` 在 www.jmjc.tech 的页面下请求 jmjc.tech 服务器的内容，是不允许的。

`2. 协议相同` https 和 http 也是两个不同的范围区域。

`3. 端口相同` 默认是 80 端口。

------

## 跨域

由于浏览器为了安全规定了 `同源策略`，绕过同源策略的限制，通常有以下几种办法。

```js
1. flash
2. 在同源域名假设一个代理服务器
3. cors
4. jsonp
```

------

## CORS

CORS 是一种 `白名单机制`，CORS 的请求成功与否取决于服务器是否同意当前域的请求，通过在服务器设置允许当前域名请求做到 `跨域访问`。

在服务器的响应头部标示 Access-Control-Allow-Origin：当前域名 or * 。

------

## JSONP

JSONP 的跨域访问是利用了 `script` 文件的加载，所有只能支持 `GET请求`，返回过来的是一个 `JavaScript 文件`。

```js
<!-- 通过 script 能跨域加载 javascript 脚本的这一特性 -->
<script src="http://xxx.com?xxx"></script> 

<!-- 假设 http://xxx.com?xxx 加载的内容 -->
<script>
 function f() {
  return 'date' // 返回一个我们需要的数据      
 }
</script>

<!-- 使用数据 -->
<script>
 f() // 'date'
</script>
```

# JavaScript 事件

## 事件

事件机制是 `UI 编程` 一个非常重要的特性，我们日常使用手机APP、桌面软件，点击了一个按钮的背后，就是触发了一个点击事件处理。JavaScript 的本质上也是一门 `UI 编程语言`，所有内置了功能非常丰富的事件对象。

------

## 执行

事件执行的两种方法。

```js
<!-- 1. html 属性绑定事件 -->
<p onclick="alert('点击事件')">按钮</p>

<!-- 2. dom 绑定事件 -->
<script>
 var p = document.getElementsByTagName('p')[0]
 p.onclick = function(e) {
  e // 当前事件对象，例如有些对象 "keydown" 按下键盘，可以通过 e 这个对象获取到 按键码，或者 "mousedown" 鼠标点击左键还是右键，“ mouseover” 当前光标坐标 ...
  this // 代表了当前元素 "p"
 }
</script>
```

------

## 事件对象

常用的事件对象。

```js
// click 点击
// load 加载
// focus 触发焦点
// blur 离开焦点
// change 改变
// submit 表单提交
// reset 表单重置
// resize 窗口大小改变
// mouseover 鼠标移入
// mouseout 鼠标移除
// scroll 滚动条
```

# JQuery 教程

## 前言

在 [JavaScript 教程](https://www.jmjc.tech/less/34) 的开始，我们描述过 `JQuery`，它是第一代 JavaScript 框架，解决了 DOM 的问题。

在 IE9 之前的浏览器时代，IE 浏览器占领了市场主导的地位，但是由于每一个 IE 浏览器的版本，都是捆绑在 Windows 操作系统的上面，更新的速度同操作系统，几年一次，导致了版本与版本之间的跨度非常大，相互之间不能兼容。这段时间就是前端人员的黑暗岁月，经常需要为每一个特定的浏览器版本，编写一份特定的代码。

JQuery 就是在这个背景下诞生的，它是一个 `DOM 库`，同它写出来的 `DOM 代码` 可以兼容所有的浏览器，大大的解放了生产力，所有迅速的流行。

今天的 JQuery 还是有很大的市场份额，但已经不是再是当年的唯一主导地位，一方面是因为 `ES6` 之后的 JavaScript 语法逐渐变得越发友好，加上现代浏览器的统一，[ JavaScript 原生 DOM 操作](https://www.jmjc.tech/less/78) 已经没有那么的反人类。还有第二代前端框架 `Vue & Raect` 的流行，挤压掉了很大 JQuery 的应用场景。

虽然如此，但是作为前端人员还是很有必要学习 JQuery 的。第一，它并未完全过时。一些如 `Bootstrap` 的流行框架还是建立在 JQuery 的基础上。第二，足够小的、没必要使用 `组件化框架` 的项目，使用它来编写，还是非常高效简洁的，`JMJC.TECH` 前端用的就是 JQuery。第三，它的一些 `DOM 思想` 一直都在。

## 运行 JQuery

在 [JQuery](http://jquery.com/) 的官网下载一个最新的版本，或者找到一家免费的公用 [CDN](https://cdn.baomitu.com/) 提供商，通过 script 标签引入之后，就可以执行 JQuery 的代码。

```html
<!DOCTYPE html>
<html>
<head>
 <title>引入 JQery</title>
</head>
 <!-- cdn.baomitu.com 360 奇舞团 提供的免费 CDN 服务 -->
 <script type="text/javascript" src="https://lib.baomitu.com/jquery/2.2.4/jquery.min.js"></script>
<body>
</body>
</html>
```

------

## 执行顺序

DOM 的操作，必须等待页面的 DOM 加载完成，如果把 JavaScript 代码，写在 HTML 元素之前，那是获取不到 DOM 元素的。

```html
<!DOCTYPE html>
<html>
<head>
 <title>执行顺序</title>
</head>
<body>
	
 <script type="text/javascript">
  alert(document.getElementsByTagName('div')[0]) // undefined
 </script>

 <div>...</div>

</body>
</html>
```

------

## load 事件

等待页面元素加载完成，触发的事件。

```html
<!DOCTYPE html>
<html>
<head>
 <title>load 事件</title>
</head>
<body>

 <script type="text/javascript">
  window.onload = function() {
   alert(document.getElementsByTagName('div')[0]) // [object HTMLDivElement]
  }
 </script>

 <div>...</div>

</body>
</html>
```

这样就能获取得到后面的 div 元素。但是存在着一个问题，就是 `load 事件` 等待的是整个页面的元素都加载完毕才会触发，如果页面的元素足够的多，这个过程会耗时很久，照成了 JavaScript 执行卡顿。

由于网页的加载，是有 `加载级别` 的，我们可以把需要加载的元素归类，例如等待 `DOM` 加载完成完毕，就马上触发。DOM 通常只有很小的 `几K` 所有整个过程就会非常的快。

DOM 的加载完成挂载的是 `DOMContentLoaded 事件`，这一步通过 JQuery 来实现就非常简单。

------

## $

`$` 就是 `JQuery 对象`，通过它，我们就可以调用 `JQuery库` 的方法。

```html
<!DOCTYPE html>
<html>
<head>
 <title>$</title>
</head>
<script type="text/javascript" src="https://lib.baomitu.com/jquery/2.2.4/jquery.min.js"></script>
<body>

 <script type="text/javascript">
  $(function() { // 这个代码块执行的，就是 DOM 被加载完毕触发
   alert(document.getElementsByTagName('div')[0]) // [object HTMLDivElement]
  })
 </script>

 <div>...</div>

</body>
</html>
```

总结一点 `JQuery 是什么` 就是基于 DOM 并且优化了 DOM 的操作。

## DOM

把 [JavaScript DOM](https://www.jmjc.tech/less/78) 的操作用 JQuery 的方法从新实现一遍。

------

## 获取元素

```js
// id
$('#id')

// class
$('.className')

// tagName
$('tag')

/*
 上面三个对应的就是 getElements... 三个方法
*/
```

------

```js
二级查找
/*
例如这种结构
<div>
 <p>...</p>
</div>
*/

// 下面两种是JQuery 二级查找的方法，JQuery 的选择器语法可以参考 “CSS 教程 - 选择器”
// $('div p') 返回的是一个 JQuery 对象，里面包含了元素的集合，$('div p')[0] 通过索引可以获取到集合里面的元素 [object HTMLParagraphElement]
$('div p')
$('div').find('p')
```

------

```js
对象筛选
$('div').parent() // 当前元素的父元素
$('div').first() // 元素集合的第一个元素
$('div').last() // 元素集合的最后一个元素
$('div').eq(0) // 指定获取元素集合中第几个元素
$('div').next() // 当前元素的下一个元素
$('div').prev('.active') // 过滤掉 class=".active" 的 div 元素
```

------

```js
元素遍历
/*
 <ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
 </ul>
*/

// each 方法
$('ul li').each(function(index, li) {
 console.log(index) // 当前索引
 console.log(li) // 当前元素
})

/*
遍历结果
0 | <p>1</p>
1 | <p>2</p>
2 | <p>3</p>
*/
```

------

## 操作元素

```js
内容
/*
 <div>
  <p>内容</p>
 </div>
*/

console.log($('div').eq(0).html()) // <p>内容</p> | 获取 div 里面的所有内容，包括 HTML
console.log($('div').eq(0).text()) // 内容 | 获取文本内容
		
$('div').eq(0).html('为空是获取，写上内容就是修改')

/*
 $().eq().find().css()... 只要返回的结果是 JQuery 对象，就能一直 “.” 下去
 这样特性在 JQuery 中被称为 “连缀”
*/
```

------

```js
属性
$().attr('class') // 获取属性
$().attr('class', 'red') // 修改属性
$().removeAttr() // 移除属性
```

------

```js
样式
$().css('color', '#ccc') // 设置颜色
$().css('background', '#ccc') // 设置背景颜色，语法同 “css”
```

------

```js
大小
/*
 大小是一组方法 .width() & .height()
*/

$(window).width() // 浏览器窗口大小
$(document).width() // 内容可视区域大小
$('div').width() // 指定区域大小
```

------

## 插入元素

```js
// <ul></ul>

// 下级插入
$('ul').prepend('<li>1</li>') // 开头
$('ul').append('<li>2</li>') // 结尾

// 同级插入
$('ul li').eq(0).after($('ul').html()) // 之后
$('ul li').eq(0).before($('ul').html()) // 之前
```

------

## 移除元素

```js
$('body').remove() // 整个页面都被移除了
```



# JQuery 表单

## 表单

同这两篇的概念类似：[JavaScript 表单](https://www.jmjc.tech/less/79)、[JavaScript 文件上传](https://www.jmjc.tech/less/80)。

------

## 选择表单

需要注意的不多。

```js
$('input')
$('select')
$('textarea')
$('[name=user]')
$('[type=checkbox]')
...
```

------

## 操作表单

JQuery 新增了一些操作表单的方法，列举常用几个。

```js
// value
$('input').val() // 获取 value 的值
$('input').val('...') // 设置

// checkbox
$('[type=radio]').prop('checked') // 是否选中
$('[type=checkbox]').attr('checked', true) // true 选中 | false 反选
$('[type=checkbox]:checked') // 获取所有选中的对象, 返回JQ集合

// select
$('select').find('option:selected').val() // 当前选中的 option
.attr('selected', 'selected') // 选中
.removeAttr('selected') // 取消选中
```

## Ajax

JQuery 对 [XMLHttpRequest 对象](https://www.jmjc.tech/less/82) 的封装更是简化到了极致，让我们能相对优雅的使用 `Ajax`。

```js
$.ajax("url", {
 // 自定义请求头
 headers: {},
 method: 'GET', // POST PUT 默认 GET
 // 请求格式 (服务器根据格式解析数据)
 contentType: 'application/json' // POST 默认 application/x-www-form-urlencoded;charset=UTF-8
 // 发送数据
 data: {}
 // 接受格式
 dataType: 'html' // json text xml
    
}).done(function(data) {
 // 成功调用
 // data 服务器返回的数据
    
}).fail(function (xhr, status) {
 // 失败调用
 // xhr, status 错误的信息

}).always(function () {
 // 无论成功失败

})
```

------

## 上传文件

上传文件其实就是构建一个 `multipart formdata` 的 HTTP 请求，需要借助 `FormData 对象`。

```js
// 构建数据
var data = new FormData()
data.append('name', $('[name=name]').val())
data.append('file', $('[name=thumb]')[0].files[0]) // file 对象

// 提交
$.ajax('url',{
 method: 'POST',
 data: data,
 processData: false, // 默认 | 不处理数据
 contentType: false // 默认 | 不设置内容类型
 ...
})

/*
 跟普通表单只有一处区别，就是普通表单的数据 data 是一个 json，上传文件是 FormData
*/
```

## 事件

JQuery 事件也是一种`连缀操作`，支持 JavaScript 标准定义的 [事件对象](https://www.jmjc.tech/less/84)。

```js
$('div').click(function() {
 alert('点我干嘛～')
})
```

------

## on & off

另一种事件执行机制。

```js
var f = function() {
 alert('点我干嘛～')
}

$('div').on('click', f) // 绑定事件
$('div').off('click', f) // 解绑事件

/*
 需要注意，下面这种写法无法解绑事件，因为两个 function 在不同的两段内存空间
*/

$('div').on('click', function() {
 alert('点我干嘛～')
})

$('div').off('click', function() {
 alert('点我干嘛～')
})
```