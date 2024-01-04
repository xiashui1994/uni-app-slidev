---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: prism
lineNumbers: true
selectable: true
drawings:
  persist: false
transition: slide-left
title: uni-app
mdc: true
---

<div class="flex items-center justify-center">
  <img src="/logo.png" />
</div>

# uni-app

<h5>一次编写，到处运行</h5>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/xiashui1994/uni-app-slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
transition: fade-out
---

# Web 标准构成

> Web标准不是某一个标准，而是由W3C和其他标准化组织制定的一系列标准的集合。主要包括结构（Structure）、表现（Presentation）和行为（Behavior）三个方面。

<br />

- 结构标准：结构用于对网页元素进行整理和分类，主要包括XML和XHTML两个部分。
- 样式标准：表现用于设置网页元素的版式、颜色、大小等外观样式，主要指的是CSS。
- 行为标准：行为是指网页模型的定义及交互的编写，主要包括DOM和ECMAScript两个部分。

<br />

<div class="flex justify-between">
  <div class="text-center">
    HTML
    <img src="/hb1.png" class="w-35" />
  </div>
  <div class="text-center">
    CSS
    <img src="/hb2.png" class="w-40" />
  </div>
  <div class="text-center">
    JavaScript
    <img src="/hb3.jpg" class="w-60" />
  </div>
</div>

---

# HTML

> HTML（英文Hyper Text Markup Language的缩写）中文译为“超文本标签语言”，主要是通过HTML标签对网页中的文本、图片、声音等内容进行描述。

<br />

#### 骨架格式
```html
<html>   
  <head>     
    <title></title>
  </head>
  <body>
  </body>
</html>
```

#### 标签分类

- 双标签

```html
<标签名> 内容 </标签名> <!-- <body>我是文字</body> -->
```

- 单标签

```html
<标签名 /> <!-- <br /> -->
```

---

# HTML

#### 标签关系

- 嵌套关系

```html
<head>
  <title></title>
</head>
```

- 并列关系

```html
<head></head>
<body></body>
```

<br />

#### 文档类型

```html
<!DOCTYPE html> <!-- html 5 -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <!-- html 4 -->
```

---
transition: slide-up
level: 2
---

# CSS

> CSS通常称为CSS样式表或层叠样式表（级联样式表），主要用于设置HTML页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、边距等）以及版面的布局等外观显示样式。

<br />

#### 样式规则

![Local Image](/gz.png)

---

# CSS

|  单位   |  说明   |
| --- | --- |
| px  | 像素 |
| em  | 相对于父元素的字体大小 |
| rem | 相对于根元素的字体大小 |
| %   | 百分比  |
| vw  | 视窗宽度百分比 |
| vh  | 视窗高度百分比 |
| rpx | 响应式 px，一种根据屏幕宽度自适应的动态单位。以 750 宽的屏幕为基准，750rpx 恰好为屏幕宽度 |

---

# CSS

|  单位   |  说明   |
| --- | --- |
| in  | 英寸 |
| cm  | 厘米 |
| mm  | 毫米 |
| pt  | 点 |

---

# CSS

#### 选择器

- 标签选择器（元素选择器）

```css
div { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

- 类选择器（类名选择器）

```css
.class { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

- ID选择器

```css
#id { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

- 通配符选择器

```css
* { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

- 伪类选择器

```css
:first-child { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

---

# CSS

#### 复合选择器

- 交集选择器

```css
div.class { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* 中间没空格 */
```

- 并集选择器

```css
div, .class { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* 逗号 */
```

- 后代选择器

```css
.class div { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* 空格分隔 */
```

- 子代选择器

```css
.class > div { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* > */
```

- 相邻兄弟选择器

```css
.class + div { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* + */
```

---

# CSS

#### 复合选择器

- 属性选择器

```css
[class=class] { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* = 全等 */
div[class^=start] { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* ^= 开始位置 */
div[class$=end] { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* $= 结束位置 */
div[class*="any"] { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; } /* *= 任意位置 */
```

- 伪元素选择器

```css
div::before { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
div::after { 属性1:属性值1; 属性2:属性值2; 属性3:属性值3; }
```

---

# CSS

#### 三大特性

- [层叠性](https://code.juejin.cn/pen/7320132139331584027)

```css
<div>层叠性</div>

<style>
  div {
    color: red;
  }
  div {
    color: blue;
  }
  div {
    color: green;
  }
</style>
```

长江后浪推前浪，前浪死在沙滩上

---

# CSS

#### 三大特性

- [继承性](https://code.juejin.cn/pen/7320132809933357066)

```css
<div>
  <span>继承性</span>
</div>

<style>
  div {
    color: red;
  }
</style>
```

龙生龙，凤生凤，老鼠生的孩子会打洞

---

# CSS

#### 三大特性

- 优先级（权重）

> 计算公式：CSS Specificity，我们称为CSS 特性或称非凡性，用一个四位的数字串(CSS2是三位)来表示，更像四个级别，值从左到右，左面的最大，一级大于一级，数位之间没有进制，级别之间不可超越

| 选择器 | 贡献值 |
| --- | --- |
| 元素（标签） | 0, 0, 0, 1 |
| 类，伪类 | 0, 0, 1, 0 |
| ID | 0, 1, 0, 0 |
| 行内样式 | 1, 0, 0, 0 |
| !important | ∞ |

---

# CSS

#### 三大特性

- [优先级（权重）](https://code.juejin.cn/pen/7320133639100956699)

```css
<div class="important" id="main">
  <span style="color: red;" class="text">优先级</span>
</div>

<style>
  * { color: white; }
  div { color: blue; }
  .important { color: green; }
  #main { color: pink; }
  .text { color: yellow;}
  .important .text { color: orange; }
  div > span { color: purple; }
  div + span { color: black; }
</style>
```

<br />

> 优先级是什么颜色？

---

# CSS

#### 盒子模型

> 所谓盒子模型就是把HTML页面中的元素看作是一个矩形的盒子，也就是一个盛装内容的容器。每个矩形都由元素的**内容**、**内边距**（padding）、**边框**（border）和**外边距**（margin）组成

<div class="flex">
  <img style="width: 50%" src="/box.png" />
  <img style="width: 50%" src="/box-ie.png" />
</div>

> box-sizing: border-box;

---

# CSS

#### 三大流

- 普通流、文档流、标准流 (normal flow)
- 浮动流 (float)
- 定位流 (position)

![Local Image](/fd.png)

---

# CSS

#### 浮动

- 浮动最早是用来控制图片，以便达到其他元素（特别是文字）实现“环绕”图片的效果
- 元素的浮动是指设置了浮动属性的元素会脱离标准普通流的控制，移动到其父元素中指定位置的过程

```css
div { float:属性值; }
```

|属性值	| 描述 |
| --- | --- |
|left	| 元素向左浮动 |
|right | 元素向右浮动 |
|none |	元素不浮动（默认值）|

<br />

> CSS3 后不再使用浮动布局，浮动只用于图文环绕

---

# CSS

#### 定位

> 元素的定位属性主要包括**定位模式**和**边偏移**

<br />

- 定位模式(定位的分类)

```css
div { position: 属性值; }
```

| 定位模式值 | 描述 |
| --- | --- |
| static | 自动定位（默认定位方式）|
| relative | 相对定位，相对于其原文档流的位置进行定位 |
| absolute | 绝对定位，相对于其上一个已经定位的父元素进行定位 |
| fixed | 固定定位，相对于浏览器窗口进行定位 |

---

# CSS

#### 定位

- 边偏移

```css
div { position: 属性值; top: 100px; left: 100px; }
```

| 边偏移属性 | 描述 |
| --- | --- |
| top | 顶端偏移量，定义元素相对于其父元素上边线的距离 |
| right | 底部偏移量，定义元素相对于其父元素下边线的距离 |
| bottom | 左侧偏移量，定义元素相对于其父元素左边线的距离 |
| left | 右侧偏移量，定义元素相对于其父元素右边线的距离 |

<br />

> 子绝父相：子级是绝对定位的话，父级要用相对定位

---

# CSS

#### 标签显示模式（display）

| 模式 | 描述 |
| --- | --- |
| block | 每个块元素通常都会独自占据一整行或多整行，可以对其设置宽度、高度、对齐等属性，常用于网页布局和网页结构的搭建 |
| inline | 不占有独立的区域，仅仅靠自身的字体大小和图像尺寸来支撑结构，一般不可以设置宽度、高度、对齐等属性，常用于控制页面中文本的样式 |
| inline-block | 在行内元素中有几个特殊的标签 **img**、**input**、**td**，可以对它们设置宽高和对齐属性 |
| none | 不显示

<br />

> 显示模式转换：display: 模式 <br />隐式转换：定位、浮动会把标签显示模式转换为块元素

---

# CSS

#### 网页布局

<br />

> 网页布局的本质：把网页元素比如文字图片等等，放入盒子里面，然后利用CSS摆放盒子的过程，就是网页布局

| 布局 | 实现方式 |
| --- | --- |
| 表格布局（已废弃）| table |
| 浮动布局（已废弃）| float |
| 定位布局 | position |
| 流式布局（百分比布局）| % |
| 响应式布局 |  rem / 媒体查询 |

---

# CSS

#### 网页布局

<br />

| 布局 | 实现方式 |
| --- | --- |
| flex布局（弹性布局）| flex |
| grid布局 | grid |

---

# CSS

#### [Flex](https://ruanyifeng.com/blog/2015/07/flex-grammar.html)

<br />

> Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性

指定为 flex 布局

```css
div { display: flex; }
```

<br />

<div class="flex justify-between">
  <div>
    <div>采用 Flex 布局的元素，称为 Flex 容器（flex container），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flex item），简称"项目"</div>
  </div>
  <img style="height: 240px" src="/flex.png" />
</div>

---

# CSS

#### Flex

<br />

##### 轴方向

- 水平的主轴（main axis）
- 垂直的交叉轴（cross axis）

<br />

##### 容器的属性

- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content

<img style="position: absolute; top: 50%; right: 40px; transform: translateY(-50%)" src="/flex.png">

---

# CSS

#### Flex-direction

<br />

> flex-direction属性决定主轴的方向（即项目的排列方向）

<br />

```css
.div { flex-direction: row | row-reverse | column | column-reverse; }
```

| 值 | 说明 |
| --- | --- |
| row（默认值）| 主轴为水平方向，起点在左端 |
| row-reverse | 主轴为水平方向，起点在右端 |
| column | 主轴为垂直方向，起点在上沿 |
| column-reverse | 主轴为垂直方向，起点在下沿 |

---

# CSS

#### Flex-wrap

<br />

> 默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行

<br />

```css
.div { flex-wrap: nowrap | wrap | wrap-reverse; }
```

| 值 | 说明 |
| --- | --- |
| nowrap（默认值）| 不换行 |
| wrap | 换行，第一行在上方 |
| wrap-reverse | 换行，第一行在下方 |

---

# CSS

#### Flex-flow

<br />

> flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap

<br />

```css
.div { flex-flow: <flex-direction> || <flex-wrap>; }
```

---

# CSS

#### Justify-content

<br />

> justify-content属性定义了项目在主轴上的对齐方式

```css
.div { justify-content: flex-start | flex-end | center | space-between | space-around; }
```

| 值 | 说明 |
| --- | --- |
| flex-start（默认值）| 左对齐 |
| flex-end | 右对齐 |
| center | 居中 |
| space-between | 两端对齐，项目之间的间隔都相等 |
| space-around | 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍 |

---

# CSS

#### Align-items

<br />

> align-items属性定义项目在交叉轴上如何对齐

```css
.div { align-items: flex-start | flex-end | center | baseline | stretch; }
```

| 值 | 说明 |
| --- | --- |
| flex-start | 交叉轴的起点对齐 |
| flex-end | 交叉轴的终点对齐 |
| center | 交叉轴的中点对齐 |
| baseline | 项目的第一行文字的基线对齐 |
| stretch（默认值）| 如果项目未设置高度或设为auto，将占满整个容器的高度 |

---

# CSS

#### Align-content

<br />

> align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

```css
.div { align-content: flex-start | flex-end | center | space-between | space-around | stretch; }
```

| 值 | 说明 |
| --- | --- |
| flex-start | 交叉轴的起点对齐 |
| flex-end | 交叉轴的终点对齐 |
| center | 交叉轴的中点对齐 |
| space-between | 两端对齐，轴线之间的间隔都相等 |
| space-around | 每根轴线两侧的间隔都相等，所以，轴线之间的间隔比轴线与边框的间隔大一倍 |

---

# CSS

#### Align-content

| 值 | 说明 |
| --- | --- |
| stretch（默认值）| 轴线占满整个交叉轴 |

<br />

#### 项目的属性

- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self

---

# CSS

#### Order

<br />

> 属性定义项目的排列顺序。数值越小，排列越靠前，默认为0

```css
.item { order: <integer>; }
```

<br />

#### Flex-grow

<br />

> flex-grow属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大

```css
.item { flex-grow: <number>; }
```

<br />

#### Flex-shrink

<br />

> flex-shrink属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小

```css
.item { flex-shrink: <number>; }
```

---

# CSS

#### Flex-basis

<br />

> flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。默认值为auto

```css
.item { flex-basis: <length> | auto; }
```

<br />

#### Flex

<br />

> flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选

```css
.item { flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]; }
```

<br />

#### Align-self

<br />

> align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性

```css
.item { align-self: auto | flex-start | flex-end | center | baseline | stretch; }
```

---

# CSS

#### 练习

<br />

- 未知盒子宽高，水平垂直居中（写出你知道的所有写法）
- 在一个盒子中，有n个子盒子，子盒子的宽高相同（例：200x300），间距相等，会自动换行，随着屏幕的宽度改变，一行显示的子盒子自动减少，当子盒子数量不能占满一行时，子盒子左对齐

---

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

> null，undefined，boolean，number，string，symbol，bigint

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
| sort(fn) / reverse | 排序与反转，改变原数组 |
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
| reduce(fn(prev, cur)， defaultPrev) | 两两执行，prev 为上次化简函数的return值，cur为当前值(从第二项开始) |
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
| import / export | es6 |
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
- 微任务： Promise.then()、async/await，MutaionObserver

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

<img style="position: absolute; right: 40px; top: 150px; width: 500px" src="/loop.awebp">

---

# JavaScript

#### Promise

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

#### Generator

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

#### Async / Await

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

> Javascript中有三种作用域：**全局作用域**、**函数作用域**、**块作用域**（ES6 引入了 let 和 const 关键字，在大括号中使用 let 和 const 声明的变量存在于块级作用域中。在大括号之外不能访问这些变量）

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
    <p>2.构造函数: 可以通过 new 来 新建一个对象 的函数</p>
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

# 宿主环境

---

# 为什么需要前端开发框架

---

# 前端开发框架组成

---

# vue2 & vue3

---

# vue 原理

---

# 微信小程序

---

# 微信生态

---

# 为什么选择 uni-app

---

# uni-app 组成

---

# uni-app & vue & 微信小程序

---

# uni-app 原理

---

# uni-app 组件

---

# uni-app API

---

# uni-app 插件市场

---

# uni_modules