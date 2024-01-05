# [Vue](https://v2.cn.vuejs.org/)

#### 介绍

<br />

> Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的**渐进式框架**

<br />

#### 特色

- 响应式
- 双向绑定
- 模板语法
- 事件处理
- 计算属性
- 生命周期
- 指令
- 单文件组件
- 插槽

---

# Vue

#### [Vue2 响应式原理](https://v2.cn.vuejs.org/v2/guide/reactivity.html)

<br />

> Vue2 采用**数据劫持**结合**发布—订阅模式**的方法，通过 **Object.defineProperty()** 来劫持 **data** 中声明的属性的 getter，setter，在数据变动时发布消息给订阅者，触发相应的监听回调，重新渲染关联的组件

<br />

<div class="grid grid-cols-2 gap-4">
    <img src="/vue2-data.png" />
    <img src="/vue2-data1.jpeg" />
</div>

---

# [Vue](https://code.juejin.cn/pen/7320456778347446298)

#### [Object.defineProperty](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)

<br />

> Object.defineProperty() 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性

```js
Object.defineProperty(obj, prop, desc) // obj 需要定义属性的当前对象 prop 当前需要定义的属性名 desc 属性描述符

// 示例
const obj = {}
Object.defineProperty(obj, 'a', {
  value: 1
})
console.log(obj) // { a: 1 }

// 数据劫持示例
const obj = {}
Object.defineProperty(obj, 'a', {
  get() {  console.log('get') },
  set() { console.log('set') }
})
console.log(obj.a) // get
obj.a = 2 // set
```

---

# Vue

#### Object.defineProperty

<br />

> 优点

<br />

- 可以检测对象中数据发生的修改

<br />

> 缺点

<br />

| 缺点 | 解决方案 |
| --- | --- |
| 无法检测到对象属性的新增或删除 | Vue.set 和 Vue.delete |
| 无法监听数组的变化 | vue2 重写了数组的 push/pop、shift/unshift、splice、sort、reverse 方法 |

---

# Vue

#### [发布/订阅模式](https://code.juejin.cn/pen/7320465699192143887)

<br />

> 我们假定，存在一个"**信号中心**"，某个任务执行完成，就向信号中心"**发布**"(publish)一个信 号，其他任务可以向信号中心"**订阅**"(subscribe)这个信号，从而知道什么时候自己可以开始执行。这就叫做"发布/订阅模式"(publish-subscribe pattern)

<br />

#### [观察者模式](https://code.juejin.cn/pen/7320493968175661096)

<br />

> 多个对象间存在一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并被自动更新

<div class="grid grid-cols-2 gap-4">
  <div>
    <p>观察者模式是由具体目标调度，比如当事件触发，目标(发布者)就会去调用观察者的方法，所以观察者模式的订阅者与发布者之间是存在依赖的</p>
    <p>发布/订阅模式由统一调度中心调用，因此发布者和订阅者不需要知道对方的存在</p>
  </div>
  <img style="height: 220px" src="/subscribe.png" />
</div>

---

# Vue

#### 虚拟DOM (Virtaul DOM)

<br />

> 用 js 对象模拟的，保存当前视图内所有 DOM 节点对象基本描述属性和节点间关系的树结构

<br />

- 维护视图和状态的关系
- 对新老虚拟 DOM 进行 Diff，以最小代价更新 DOM，减少浏览器的重绘及回流，提升渲染性能
- 除了渲染 DOM，还可以实现 SSR(Nuxt.js/Next.js)、原生应用(Weex/React Native)、小程序(mpvue/uni-app)

```js
// 标签
<div><a>click me</a></div>
// 虚拟DOM
{
  tag: 'div',                 /*说明这是一个div标签*/
  children: [                 /*存放该标签的子节点*/
    {
      tag: 'a',           /*说明这是一个a标签*/
      text: 'click me'    /*标签的内容*/
    }
  ]
}
```

---

# Vue

#### [生命周期](https://v2.cn.vuejs.org/v2/guide/instance.html#%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E5%9B%BE%E7%A4%BA)

| 生命周期 | 描述 |
| --- | --- |
| beforeCreate | 在实例初始化之前被调用，创建前状态 |
| created | 在实例创建之后被调用，创建后状态 |
| beforeMount | 在挂载之前被调用，渲染前状态 |
| mounted | 在挂载之后被调用，渲染后状态 |
| beforeUpdate | 数据更新时被调用，更新前状态 |
| updated | 数据更新时被调用，更新后状态 |
| beforeDestroy | 实例销毁之前被调用 |

---
layout: two-cols
---

# Vue

#### 生命周期

| 生命周期 | 描述 |
| --- | --- |
| destroyed | 实例销毁之后被调用 |
| activated | 被 keep-alive 缓存的组件激活时调用 |
| deactivated | 被 keep-alive 缓存的组件停用时调用 |

<br />

> created：组件初始化完毕，可以访问各种数据，获取接口数据等 mounted：实例已经挂载完成，可以进行一些DOM操作

::right::

<div class="flex justify-center">
  <img style="height: 520px;" src="/lifecycle.png" />
</div>

---

# Vue

#### [组件](https://v2.cn.vuejs.org/v2/guide/components.html)

<br />

> 组件是可复用的 Vue 实例

<br />

- 组件化开发能大幅提高开发效率、测试性、复用性等
- 降低更新频率，只重新渲染变化的组件
- 组件的特点：高内聚、低耦合、单向数据流

<img style="height: 260px;" src="/components.png">

---

# Vue

#### 组件

```js
<template>
  <div>
    <span>{{ msg }}</span>
  </div>
</template>
<script>
export default {
  name: 'HelloWorld', // 组件名
  props: {}, // 组件参数
  data() {
    return {
      msg: 'Hello World'
    }
  },
  methods: {},
  mounted() {}
}
```

> 组件和页面接收的选项基本一致，组件可以通过 props 传递参数，并通过 name 属性定义组件的名称

---

# Vue

#### [组件注册](https://v2.cn.vuejs.org/v2/guide/components-registration.html)

<br />

> 组件注册类型：**全局注册**和**局部注册**

<br />

```js
import HelloWorld from './components/HelloWorld.vue'

// 全局注册
Vue.component('HelloWorld', HelloWorld)

// 局部注册
export default {
  components: {
    HelloWorld
  }
}
```

