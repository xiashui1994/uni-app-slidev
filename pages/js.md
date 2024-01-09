# JavaScript

<br />

### Javascript 组成

<br />

| 组成部分 | 描述 |
| --- | --- |
| ECMAScript | ECMA 欧洲计算机制造联合会，定义了JavaScript的语法规范，JavaScript的核心，描述了语言的基本语法和数据类型，ECMAScript是一套标准，定义了一种语言的标准与具体实现无关 |
| DOM（文档对象模型） | 一套操作页面元素的API，DOM可以把HTML看做是文档树，通过DOM提供的API可以对树上的节点进行操作 |
| BOM（浏览器对象模型） | 一套操作浏览器功能的API，通过BOM可以操作浏览器窗口，比如：弹出框、控制浏览器跳转、获取分辨率等 |

---

# JavaScript

#### 数据类型

<br />

- 基本数据类型

> null，undefined，boolean，number，string，[symbol](https://www.bookstack.cn/read/es6-3rd/spilt.1.docs-symbol.md)，[bigint](https://www.bookstack.cn/read/es6-3rd/spilt.9.docs-number.md)

<br />

- 引用数据类型

> Object（包含普通对象-Object，数组对象-Array，正则对象-RegExp，<br />日期对象-Date，数学函数-Math，函数对象-Function）

<img style="position: absolute; top: 50%; right: 40px; width: 400px; transform: translateY(-50%);" src="/type.png">

---

# JavaScript

#### 数据类型转换

<br />

> 在 JS 中类型转换只有三种情况，分别是：转换为布尔值、转换为数字、转换为字符串

<br />

<img style="width: 450px" src="/type-1.png">

---

# JavaScript

#### 隐式类型转换

<br />

| 条件 | 描述 |
| --- | --- |
| 逻辑运算符：&&、\|\|、！| 转换为布尔值 |
| 运算符：+、-、*、/、% | + 视情况而定，其它一律转换成数值后计算 |
| 关系操作符：>、<、<=、>= | 转换为数值 |
| 相等运行算符：== | 视情况而定 |
| if / while 条件 | 转换为布尔值  |

---

# JavaScript

#### == 的隐式类型转换

<br />

- 类型相同，则无需进行类型转换。
- 如果其中一个操作数是 null 或者 undefined ，那么另一个操作数必须是 null 或者 undefined 才会返回 true ，否则返回 false 。
- 如果其中一个操作数是 Symbol ，那么返回 false。
- 如果两个操作数都为 string 和 number 类型，那就就将字符串转换为 number。
- 如果一个操作数是 boolean 类型，那么转换成 number。
- 如果一个操作数为 object ，且另一方为 string、number、或者 Symbol ，就会把object 转换为原始类型再进行判断。

---

# JavaScript

#### + 的隐式类型转换

<br />

> +号操作符，不仅可以用作数字相加，还可以用作字符串拼接

<br />

- 如果其中一个操作数是 string，另外一个操作数是 undefined、null 或者 boolean，则调用 toString() 方法进行字符串拼接。
- 如果是纯对象、数组、正则等，则默认调用对象的转换方法，会存在优先级，然后再进行拼接。
- 如果其中有一个是 number ，另外一个是 undefined、null、boolean、number，则会将其转换为数字进行加法运算，对象的情况参考上一条规则。
- 如果其中一个是 string ，一个是 number，则按照字符串规则进行拼接。

---

# JavaScript

#### 数组常用方法

<br />

| 方法 | 说明 |
| --- | --- |
| map | 遍历数组，返回回调返回值组成的新数组 |
| forEach | 遍历数组，无法break，可以用try/catch中throw new Error来停止 |
| filter | 过滤 |
| some | 有一项返回true，则整体为true |
| every | 有一项返回false，则整体为false |
| join | 通过指定连接符生成字符串 |

---

# JavaScript

#### 数组常用方法

<br />

| 方法 | 说明 |
| --- | --- |
| push / pop | 末尾推入和弹出，改变原数组， 返回推入/弹出项 |
| unshift / shift | 头部推入和弹出，改变原数组，返回操作项 |
| sort / reverse | 排序与反转，改变原数组 |
| concat | 连接数组，不影响原数组， 浅拷贝 |
| slice | 返回截断后的新数组，不改变原数组 |
| splice | 返回删除元素组成的数组，value为插入项，改变原数组 |

---

# JavaScript

#### 数组常用方法

<br />

| 方法 | 说明 |
| --- | --- |
| indexOf / lastIndexOf | 查找数组项，返回对应的下标 |
| reduce(fn(prev, cur)， defaultPrev) | 对数组中的每个元素执行一个指定的回调函数，将数组元素进行累积计算，最终返回一个值。 |
| includes | 返回一个布尔值，表示某个数组是否包含给定的值 |
| find | 返回第一个符合条件的项 |
| findIndex | 返回第一个符合条件的项的下标 |
| ... | 扩展运算符，将一个数组转为用逗号分隔的参数序列 |

---

# JavaScript

#### 函数

<br />

> 函数是一等公民，可以作为参数传递，也可以作为返回值返回

<br />

- 函数的定义

```js
function 函数名() { } // 函数声明
let 函数名 = function() { } // 函数表达式
let 函数名 = () => { } // 箭头函数
```

- 函数的调用

```js
函数名()
```

- 函数的参数

```js
function 函数名(形参1, 形参2, 形参3...) {}
```

---

# JavaScript

#### 函数

<br />

- 函数的返回值

```js
function 函数名() { return 返回值 }
let 变量 = function 函数名() { return 返回值 } // 变量接收函数的返回值
```

- 匿名函数

```js
function () { }
() => {}
```

- 自调用函数

```js
(function() { })()
```

---

# JavaScript

#### 模块化

<br />

> 模块化开发在现代开发中已是必不可少的一部分，它大大提高了项目的可维护、可拓展和可协作性。通常，我们在浏览器中使用 ES6 的模块化支持，在 Node 中使用 commonjs 的模块化支持

| 分类 | 说明 |
| --- | --- |
| [import](https://www.bookstack.cn/read/es6-3rd/spilt.4.docs-module.md) / [export](https://www.bookstack.cn/read/es6-3rd/spilt.3.docs-module.md) | es6 |
| require / module.exports / exports | commonjs |
| require / defined | amd |

<br />

- require支持 动态导入，import不支持，正在提案 (babel 下可支持)
- require是 同步 导入，import属于 异步 导入
- require是 值拷贝，导出值变化不会影响导入值；import指向 内存地址，导入值会随导出值而变化

---

# JavaScript

#### 异步编程

<br />

> JS是一门单线程语言，单线程就意味着，所有的任务需要排队，前一个任务结束，才会执行下一个任务。这样所导致的问题是：如果JS执行的时间过长，这样就会造成页面的渲染不连贯，导致页面渲染加载阻塞的觉。为了解决这个问题，JS中出现了同步和异步

<br />

- 同步任务：即主线程上的任务，按照顺序由上⾄下依次执⾏，当前⼀个任务执⾏完毕后，才能执⾏下⼀个任务
- 异步任务：不进⼊主线程，⽽是进⼊任务队列的任务，执行完毕之后会产生一个回调函数，并且通知主线程。当主线程上的任务执行完后，就会调取最早通知自己的回调函数，使其进入主线程中执行

<br />

> 异步任务分为：**宏任务**(macro-task)和**微任务**(micro-task)

<br />

- 宏任务： script( 整体代码)、setTimeout、setInterval、I/O、UI 交互事件
- 微任务： Promise.then()、async/await，[MutaionObserver](https://developer.mozilla.org/zh-CN/docs/Web/API/MutationObserver)

---

# JavaScript

#### Event Loop

<br />

> Event Loop：事件循环又叫事件队列

1.进入到script标签，就进入到了第一次事件循环

2.遇到同步代码，立即执行

3.遇到宏任务，放入到宏任务队列里

4.遇到微任务，放入到微任务队列里

5.执行完所有同步代码

6.执行微任务代码

7.微任务代码执行完毕，本次队列清空，寻找下一个宏任务，重复步骤1

> 以此反复直到清空所以宏任务，这种不断重复的执行机制，就叫做事件循环

<img style="position: absolute; right: 40px; top: 150px; width: 500px" src="/loop.png">

---

# JavaScript

#### [Promise](https://www.bookstack.cn/read/es6-3rd/spilt.1.docs-promise.md)

<br />

> Promise 是异步编程的一种解决方案，所谓 Promise，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果

<br />

#### Promise对象有以下两个特点

- 对象的状态不受外界影响。Promise 对象代表一个异步操作，有三种状态：**pending**（进行中）、**fulfilled**（已成功）和 **rejected**（已失败）。只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态

- 一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise 对象的状态改变，只有两种可能：从 pending 变为fulfilled 和从 pending 变为 rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果，这时就称为 resolved（已定型）

---

# JavaScript

#### Promise.prototype.then()

<br />

> then 方法接收两个参数，第一个参数是 resolved 状态的回调函数，第二个参数（可选）是 rejected 状态的回调函数，返回一个新的 Promise 对象，因此可以采用链式写法

<br />

#### Promise.prototype.catch()

<br />

> 指定发生错误时的回调函数，回调函数的参数是错误对象，返回一个新的 Promise 对象

<br />

#### Promise.prototype.finally()

<br />

> 指定不管 Promise 对象最后状态如何，都会执行的操作

---

# JavaScript

#### Promise.all()

<br />

> 接收一个 promise 的 iterable 类型（注：Array，Map，Set 都属于 ES6 的 iterable 类型）的输入，并且只返回一个  Promise 实例，输入的所有 promise 的 resolve 回调的结果是一个数组，只要任何一个输入的 promise 的 reject 回调执行或者输入不合法的 promise 就会立即抛出错误，并且 reject 的是第一个抛出的错误信息

<br />

#### Promise.race()

<br />

> 接收一个 promise 的 iterable 类型（注：Array，Map，Set 都属于 ES6 的 iterable 类型）的输入，并且只返回一个  Promise 实例，一旦输入中有一个 promise 被 resolve 或者 reject 就会立刻返回

---

# JavaScript

#### [Generator](https://www.bookstack.cn/read/es6-3rd/spilt.1.docs-generator.md)

<br />

> Generator 函数是 ES6 提供的一种异步编程解决方案，语法行为与传统函数完全不同。Generator 函数是一个状态机，封装了多个内部状态，执行 Generator 函数会返回一个遍历器对象，可以依次遍历 Generator 函数内部的每一个状态

<br />

- 声明

> 与函数声明类似，不同的是function关键字与函数名之间有一个星号，以及函数体内部使用yield表达式，定义不同的内部状态（yield在英语里的意思就是“产出”）

```js
function* gen(x) {
 const y = yield x + 6;
 return y;
}
```

- [执行](https://code.juejin.cn/pen/7320136919236083762)

```js
const g = gen(1); // 执行 Generator 会返回一个 Object,而不是像普通函数返回 return 后面的值
g.next(); // { value: 7, done: false }
g.next(); // { value: undefined, done: true }
```

---

# JavaScript

#### Generator

<br />

> 调用 Generator 函数后，该函数并不执行，返回的也不是函数运行结果，而是一个指向内部状态的指针对象，也就是遍历器对象（Iterator Object）。下一步，必须调用遍历器对象的 next 方法，使得指针移向下一个状态

```js
function *fetch() {
  yield ajax('aaa')
  yield ajax('bbb')
  yield ajax('ccc')
}
let gen = fetch()
let res1 = gen.next() // { value: 'aaa', done: false }
let res2 = gen.next() // { value: 'bbb', done: false }
let res3 = gen.next() // { value: 'ccc', done: false }
let res4 = gen.next() // { value: undefined, done: true } done 为 true 表示执行结束
```

> ES6 没有规定，function 关键字与函数名之间的星号，写在哪个位置，下面的写法都能通过

```js
function * fetch() { }
function *fetch() { }
function* fetch() { }
function*fetch() { }
```

---

# JavaScript

#### [Async / Await](https://www.bookstack.cn/read/es6-3rd/spilt.1.docs-async.md)

<br />

> async/await 其实就是 Generator 的语法糖，async 函数其实就相当于 function * 的作用，而 await 就相当与 yield 的作用。在 async/await 机制中，包含了 [spawn](https://www.bookstack.cn/read/es6-3rd/spilt.4.docs-async.md) 自动执行函数

async 函数对 Generator 函数的改进体现在以下四点：

<p style="font-size: 16px">1.内置执行器：async 函数执行与普通函数一样，不像 Generator 函数，需要调用 next 方法，或使用 <a href="https://www.bookstack.cn/read/es6-3rd/spilt.5.docs-generator-async.md" target="_blank">co模块</a> 才能真正执行</p>
<p style="font-size: 16px">2.语意化更清晰：async 和 await，比起星号和 yield，语义更清楚了。async 表示函数里有异步操作，await 表示紧跟在后面的表达式需要等待结果</p>
<p style="font-size: 16px">3.适用性更广：<a href="https://www.bookstack.cn/read/es6-3rd/spilt.5.docs-generator-async.md" target="_blank">co模块</a> 约定，yield 命令后面只能是 <a href="https://www.bookstack.cn/read/es6-3rd/spilt.4.docs-generator-async.md" target="_blank">Thunk函数</a> 或 Promise 对象，而 async 函数的 await 命令后面，可以是 Promise 对象和原始类型的值（数值、字符串和布尔值，但这时会自动转成立即 resolved 的 Promise 对象）</p>
<p style="font-size: 16px">4.返回值是 Promise：async 函数的返回值是 Promise 对象，这比 Generator 函数的返回值是 Iterator 对象方便多了。你可以用 then 方法指定下一步的操作</p>

---

# JavaScript

#### async 函数

> async 函数的返回值为 Promise 对象，所以它可以调用 then 方法

```js
async function fn() {
  return 'async'
}
fn().then(res => {
  console.log(res) // 'async'
})
```

<br />

#### await 表达式

> await 右侧的表达式一般为 promise 对象，但也可以是其它的值

- 1.如果表达式是 promise 对象，await 返回的是 promise 成功的值
- 2.如果表达式是其它值，直接将此值作为 await 的返回值
- 3.await 后面是 Promise 对象会阻塞后面的代码，Promise 对象 resolve，然后得到 resolve 的值，作为 await 表达式的运算结果

---

# JavaScript

#### 闭包

<br />

> 闭包是指有权访问另外一个函数作用域中的变量的函数，闭包产生的本质就是，当前环境中存在指向父级作用域的引用

<br />

> Javascript中有三种作用域：**全局作用域**、**函数作用域**、**[块作用域](https://www.bookstack.cn/read/es6-3rd/spilt.2.docs-let.md)**（ES6 引入了 let 和 const 关键字，在大括号中使用 let 和 const 声明的变量存在于块级作用域中。在大括号之外不能访问这些变量）

```js
var a = 1; // 全局作用域
function f1() { // 函数作用域
  let a = 2
  function f2() {
    console.log(a); // 2
  }
  return f2;
}
const x = f1();
x();
```

> 在这段代码中，f1 的作用域指向有全局作用域和它本身，f2 的作用域指向全局作用域（window）、f1 和它本身。作用域是从最底层向上找，直到找到全局作用域（window）为止，如果全局还没有的话就会报错

---

# JavaScript

#### 原型/构造函数/实例

<br />

<div class="flex items-center justify-between">
  <div style="width: 350px">
    <p>1.原型（prototype）: 一个简单的对象，用于实现对象的属性继承。可以简单的理解成对象的爹。在 Firefox 和 Chrome 中，每个JavaScript对象中都包含一个 __proto__(非标准) 的属性指向它爹(该对象的原型)，可 obj__proto__  进行访问</p>
    <p>2.构造函数: 可以通过 new 来新建一个对象的函数（任何一个函数，如果在前面加了new，那就是构造函数）</p>
    <p>3.实例: 通过构造函数和 new 创建出来的对象，便是实例。 实例通过 __proto__ 指向原型，通过 constructor 指向构造函数</p>
  </div>
  <img style="width: 500px" src="/constructor.png">
</div>

---

# JavaScript

#### 原型链

<br />

> JavaScript 对象通过 **\_\_proto\_\_** 指向父类对象，直到指向 Object 对象为止，这样就形成了一个原型指向的链条，即原型链

<img style="margin-left: -80px" src="/proto.png" />

---

# JavaScript

#### this 指向

<br />

| 调用方式 | 非严格模式 |	备注 |
| --- | --- |	--- |
| 全局作用域 | window |
| 普通函数调用 | window |	严格模式下是 undefined |
| 构造函数调用 | 实例对象 |	原型方法中 this 也是实例对象 |
| 对象方法调用 | 该方法所属对象 |	紧挨着的对象 |
| 事件绑定方法 | 绑定事件对象	|
| 箭头函数 | 继承自外部作用域，不改变 this 指向 |

---

# JavaScript

#### DOM

<br />

> DOM(Document Object Model) 是一套用于操作页面元素的 API，可以把 HTML 看做是文档树，通过 DOM 提供的 API 可以对树上的节点进行操作

<br />

#### DOM节点类型

- Document 节点，整个文档是一个文档节点
- Element 节点，每个 HTML 标签是一个元素节点
- Attribute 节点，每一个 HTML 属性是一个属性节点
- Text 节点，包含在 HTML 元素中的文本是文本节点

---

# JavaScript

#### 操作DOM

- 查找

```js
querySelector() // 通过选择器
querySelectorAll() // 通过选择器
getElementsByTagName() // 通过标签名称
getElementsByName() // 通过元素的 Name 属性的值
getElementsByClassName() // 通过类名
getElementById() // 通过元素 Id，唯一性
```

- 创建新节点

```js
createDocumentFragment() // 创建一个DOM片段
createElement() // 创建一个具体的元素
createTextNode() // 创建一个文本节点
```

- 添加、移除、替换、插入

```js
appendChild() // 添加子节点
removeChild() // 移除子节点
replaceChild() // 替换子节点
insertBefore() // 插入子节点
```

---

# JavaScript

#### 事件

<br />

> 事件三要素：事件源，事件名称，事件处理函数

<br />

| 要素 | 说明 |
| --- | --- |
| 事件源 | 触发(被)事件的元素 |
| 事件名称 | 事件的名称 |
| 事件处理函数 | 事件触发后要执行的代码(函数形式) |

---

# JavaScript

#### 注册/移除事件

```js
const box = document.querySelector('.box');

// 1.onclick
box.onclick = function () { }; // 注册
box.onclick = null; // 移除

// 2.addEventListener/removeEventListener
const fn = function () { };
box.addEventListener('click', fn, false); // 注册
box.removeEventListener('click', fn, false); // 移除
```

<br />

> 事件的三个阶段：捕获阶段、当前目标阶段、冒泡阶段

<br />

<div class="flex">
 <img style="width: 150px; margin-right: 30px" src="/click.png" />
 <img style="width: 150px" src="/bubbling.png" />
</div>

---

# JavaScript

#### 事件对象 Event

| event | 说明 |
| --- | --- |
| type | 事件类型 |
| target | 事件源 |
| clientX/clientY | 窗口位置 |
| preventDefault() | 阻止默认行为 |
| stopPropagation() | 阻止冒泡 |

---

# JavaScript

#### BOM

<br />

> 一套操作浏览器功能的 API，通过 BOM 可以操作浏览器窗口。BOM 的顶级对象是 window

<br />

| BOM | 说明 |
| --- | --- |
| 对话框 | alert()、prompt()、confirm() |
| 定时器 | setTimeout()、clearTimeout()、setInterval()、clearInterval() |
| location对象 | reload()、href、search |
| history对象 | back()、forward()、go() |
| navigator对象 | userAgent、platform |

---

# JavaScript

#### 练习

<br />

- [使用 reduce 将下面的数据根据 type 分组](https://code.juejin.cn/pen/7321564820539932682)

```js
[{ name: '苹果', type: '水果'}, { name: '香蕉', type: '水果'}, { name: '橘子', type: '水果'},
{ name: '鸡蛋', type: '蔬菜'}, { name: '土豆', type: '蔬菜'}, { name: '黄瓜', type: '蔬菜'},
{ name: '猪肉', type: '肉类'}, { name: '牛肉', type: '肉类'}, { name: '鸡肉', type: '肉类'}]

// 示例结果
{
  "水果": [ '苹果', '香蕉', '橘子'],
  "蔬菜": [ '鸡蛋', '土豆', '黄瓜'],
  "肉类": [ '猪肉', '牛肉', '鸡肉'],
}
```

- [求斐波那契数列的第n值（提示：递归）](https://code.juejin.cn/pen/7321565558511435776)