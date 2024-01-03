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

- 层叠性

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

- 继承性

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

- 优先级（权重）

```css
<div class="important" id="main">
  <span style="color: red;" class="text">优先级</span>
</div>

* { color: white; }
div { color: blue; }
.important { color: green; }
#main { color: pink; }
.text { color: yellow;}
.important .text { color: orange; }
div > span { color: purple; }
div + span { color: black; }
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

#### Flex

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
    <br />
    <a href="https://ruanyifeng.com/blog/2015/07/flex-grammar.html" target="_blank">Flex 布局教程</a>
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