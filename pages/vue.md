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
layout: two-cols
---

# Vue

#### 模板编译

<br />

> Vue 的编译过程就是将 template 转化为 render 函数的过程

- 解析生成 AST树：将 template 模板转化成 AST语法树，使用大量的正则表达式对模板进行解析，遇到标签、文本的时候都会执行对应的钩子进行相关处理

- 标记优化：对静态语法做静态标记，静态节点跳过 diff 操作

- 代码生成：将优化后的 AST树转换为可执行的代码

> 相关概念：[render 函数](https://juejin.cn/post/6844903973502058504)、[AST抽象语法树](https://juejin.cn/post/7155151377013047304)、[diff 算法](https://juejin.cn/post/6844903607913938951)

:: right ::

```js
<div id="app"></div>
let vm = new Vue({
  el: '#app',
  template: `<div>
    // <span>hello world</span> 是静态节点
    <span>hello world</span>    
    // <p>{{name}}</p> 是动态节点
    <p>{{name}}</p>
  </div>`,
  data() { return { name: 'test' } }
});

// 把 html 字符串变成 render 函数
export function compileToFunctions(template) {
  // 1.把 html 代码转成 ast语法树 ast 用来描述代码本身形成树结构不仅可以描述 html 也能描述 css 以及 js 语法
  let ast = parse(template); // template 转 ast语法树
  // 2.优化静态节点：对 ast树进行标记，标记静态节点
  if (options.optimize !== false) { optimize(ast, options); }
  // 3.通过 ast 重新生成代码
  // 类似 _c('div',{id:"app"},_c('div',undefined,_v("hello"+_s(name)),_c('span',undefined,_v("world"))))
  // _c代表创建元素 _v代表创建文本 _s代表 Json.stringify --把对象解析成文本
  let code = generate(ast);
  // 使用 with 语法改变作用域为 this 之后调用 render 函数可以使用 call 改变 this 方便 code 里面的变量取值
  let renderFn = new Function(`with(this){return ${code}}`);
  return renderFn;
}
```

---

# Vue

#### [虚拟DOM (Virtaul DOM)](https://github.com/snabbdom/snabbdom)

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

---
layout: two-cols
---

# Vue

#### 组件通信

<br />

> props/$emit

<br />

- 父组件通过 props 向子组件传递数据
- 子组件通过 $emit 向父组件发送事件

<br />

```js
// 子组件代码
props: ['messageFromParent'],  // 通过 props 接收父组件传过来的消息
data() {
  return {
    message: ''
  }
},
methods: {
  send() {
    this.$emit('on-receive', this.message)  // 通过 $emit 触发 on-receive 事件，调用父组件中 receive 回调，并将 this.message 作为参数
  }
}
```

:: right ::

```js
// 父组件代码
<Child :messageFromParent="message" @on-receive="receive" />
...
data() {
  return {
    message: '', // 传递给子组件的消息
    messageFromChild: ''
  }
},
methods: {
  receive(msg) { // 接受子组件的信息，并将其赋值给 messageFromChild
    this.messageFromChild = msg
  }
}
...
```

---
layout: two-cols
---

> v-slot

<br />

- 父组件通过 \<template v-slot:child\>{{ message }}\</template\> 将父组件的 message 值传递给子组件
- 子组件通过 \<slot name="child"></slot\> 接收到相应内容

```js
// 子组件代码
<template>
  <div class="child">
    <p>收到来自父组件的消息：
      <slot name="child"></slot>  <!--展示父组件通过插槽传递的{{message}}-->
    </p>
  </div>
</template>
```

```js
// 父组件代码
<template>
  <Child>
    <template v-slot:child>
      {{ message }}  <!--插槽要展示的内容-->
    </template>
  </Child>
</template>
```

:: right ::

> [$refs/$parent/$children/$root]

<br />

- $refs 获 ref 绑定的组件
- $parent 获取父组件
- $children 获取子组件
- $root 获取根组件

```js
// $refs
this.$refs.[ref名] // 获取 ref 绑定的组件

// $parent
this.$parent // 获取父组件

// $children
this.$children // 获取子组件

// $root
this.$root // 获取根组件
```

---
layout: two-cols
---

> [$attrs/$listener]

<br />

- \$attrs 接收父作用域中不作为 prop 被识别的 attribute 属性，并且可以通过v-bind="$attrs"传入内部组件
- \$listener 包含了父作用域中的 v-on 事件监听器。它可以通过 v-on="$listeners" 传入内部组件

```js
// 孙组件
<input name="compC" type="text" v-model="message" v-on="$listeners" /> <!--将父组件 keyup 的监听回调绑在该 input 上-->

// 子组件
<input name="compB" type="text" v-model="message" v-on="$listeners" />  <!--将父组件 keyup 的监听回调绑在该 input 上-->
<CompC v-bind="$attrs" v-on="$listeners" /> <!--将父组件 keyup 的监听回调继续传递给孙组件，将父组件传递的 attrs 继续传递给孙组件-->

// 父组件
<CompB :messageFromA="message" @keyup="receive" />  <!--监听子孙组件的 keyup 事件，将 message 传递给子孙组件-->
```

:: right ::

> provide/inject

<br />

- provide 是一个对象，或者是一个返回对象的函数。该对象包含可注入其子孙的 property ，即要传递给子孙的属性和属性值
- inject 一个字符串数组，或者是一个对象。当其为字符串数组时，接收 provide 中的属性。当其为对象时，可以通过配置 default 和 from 等属性来设置默认值，在子组件中使用新的命名属性

```js
// 父组件
provide() {
  return {
    messageFromA: this.message  // 将 message 通过 provide 传递给子孙组件
  }
}

// 子组件
inject: ['messageFromA'], // 通过 inject 接受父组件中 provide 传递过来的 message
```

> provide 和 inject 默认不是响应式的，可以传入一个可监听的对象

---
layout: two-cols
---

> eventBus

<br />

- eventBus 又称事件总线，通过注册一个新的 Vue 实例，通过调用这个实例的 $emit 和 $on 等来监听和触发这个实例的事件，通过传入参数从而实现组件的全局通信

```js
// 方法一
// 抽离成一个单独的 js 文件 Bus.js ，然后在需要的地方引入
// Bus.js
import Vue from "vue"
export default new Vue()

// 方法二 直接挂载到全局
// main.js
import Vue from "vue"
Vue.prototype.$bus = new Vue()

// 示例
this.$bus.$on('event', (data) => {}) // 通过 eventBus 监听 event 事件

this.$bus.$emit('event', { message: 'hello' }) // 通过 eventBus 触发 event 事件
```

:: right ::

> [Vuex](https://v3.vuex.vuejs.org/zh/)

<br />

- Vuex 是一个状态管理器，用于管理应用的状态

```js
// store.js
import Vue from 'vue'
import Vuex from 'vuex'
export default new Vuex.Store({
  state: {
    message: ''
  },
  mutations: {
    setMessage (state, message) {
      state.message = message
    }
  }
})

// 组件
this.$store.state.message // 获取状态

this.$store.commit('setMessage', message) // 修改状态
```

---
layout: two-cols
---

# Vue

#### 组件通信

<br />

<img src="/message.png" style="height: 380px" />

:: right ::

#### 插槽

<br />

> Vue 实现了一套内容分发的 API，这套 API 的设计灵感源自 [Web Components 规范草案](https://github.com/WICG/webcomponents/blob/gh-pages/proposals/Slots-Proposal.md)，将 **\<slot>** 元素作为承载分发内容的出口

<br />

- 默认插槽

```js
// 子组件
<template>
  <div>
    <slot>我是默认插槽，没给我传内容就会默认显示这句话</slot>
  </div>
</template>

// 父组件
<template>
  <div>
    <Child>
      <p>hello</p>
    </Child>
  </div>
</template>
```

---
layout: two-cols
---

# Vue

#### 具名插槽

- 具名插槽允许我们在组件中定义多个插槽

```js
// 子组件
<template>
  <div>
    <slot name="header"></slot>
    <slot name="footer"></slot>
  </div>
</template>

// 父组件
<template>
  <Child>
    <template v-slot:header>
      <h2>我是头部内容!</h2>
    </template>
    <template v-slot:footer>
      <h2>我是底部内容!</h2>
    </template>
  </Child>
</template>
```

:: right ::

#### 作用域插槽

- 作用域插槽是一种特殊的插槽，它允许我们在插槽内部访问组件实例的数据，允许父组件将数据传递到子组件中，并在子组件中使用

```js
// 子组件
<template>
  <div>
    <slot :message="message"></slot>
  </div>
</template>
data() {
  return {
    message: 'hello'
  }
}

// 父组件
<template>
  <Child>
    <template v-slot="{ message }">
      <p>{{ message }}</p>
    </template>
  </Child>
</template>
```

---

# Vue

#### 事件处理

<br />

> 可以用 v-on 指令监听 DOM 事件，简写为 @

<br />

```js
// 写法一 直接执行js代码
<button v-on:click="counter += 1">Add 1</button>
<button @click="counter += 1">Add 1</button>

// 写法二 调用方法
<button @click="add(1)">Add 1</button>
methods: {
  add(num) {
    this.counter += num
  }
}

// $event 接收事件参数
<Child @click="add($event, 1)">Add 1</Child>
```

---

# Vue

#### 事件修饰符

<br />

- .stop 阻止事件冒泡
- .prevent 阻止默认行为
- .capture 事件捕获
- .self 仅触发自身
- .once 仅触发一次
- .passive 不阻止默认行为

<br />

#### 自定义事件

```js
// 子组件
this.$emit('message')

// 父组件
<Child @message="message"></Child>
```

---
layout: two-cols
---

# Vue

#### 计算属性

<br />

> 当页面中有某些数据依赖其他数据进行变动的时候，可以使用计算属性 computed

```js
computed: {
  message() {
    return this.message.split('').reverse()
  }
  // 接收参数
  message() {
    return (message) => message.split('').reverse()
  }
  // get set
  message: {
    get() { return this.message }, // get ⽅法是取
    set(val) { this.message = val } // 在 computed 中定义的变量的值发⽣改变时，会触发 set ⽅法
  }
}
```

> 计算属性是基于它们的响应式依赖进行**缓存**的。只在相关响应式依赖发生改变时它们才会**重新求值**

:: right ::

#### 侦听器

<br />

> 如果要在数据变化的同时进行异步操作或者是比较大的开销，那么 watch 为最佳选择

```js
watch: {
  // newVal 新值，oldVal 旧值
  message(newVal, oldVal) {}
  // 对象属性监听
  'obj.message'(newVal, oldVal) {}
  message: {
    // 回调函数
    handler(newVal, oldVal) {},
    // 深度监听
    deep: true,
    // 立即监听
    immediate: true
  }
}
```

> 无缓存性，页面重新渲染时值不变化也会执行，watch 监听性能开销很大，非必要不使用 watch

---

# Vue

#### mixin（混入）

<br />

> 复用组件功能

```js
// mixin.js
export default { ... } // 和组件选项相同

// 全局混入
import Vue from 'vue'
import mixin from './mixin.js'
Vue.mixin(mixin)

// 组件混入
import mixin from './mixin.js'
export default {
  mixins: [mixin]
}

// 选项合并
1.数据对象在内部会进行递归合并，并在发生冲突时以组件数据优先
2.同名钩子函数将合并为一个数组，混入对象的钩子将在组件自身钩子之前调用
3.值为对象的选项，将被合并为同一个对象。两个对象键名冲突时，取组件对象的键值对
```

---

# Vue

#### 自定义指令

```js
// 全局注册
import Vue from 'vue'
Vue.directive('focus', { // v-focus
  bind: function (el, binding, vnode) {},
  inserted: function (el, binding, vnode) {},
  update: function (el, binding, vnode) {}
})
// el: 绑定的元素
// binding: {
//   name: 指令名，不包括 v- 前缀
//   value: 指令的绑定值
//   oldValue: 指令绑定的前一个值
//   expression: 指令表达式
//   arg: 传给指令的参数
//   modifiers: 修饰符
// }
// vnode: Vue 编译生成的虚拟节点

// 局部注册
directives: {
  focus: { ... }
}
```

---

# Vue

#### 插件

<br />

> 插件通常用来为 Vue 添加全局功能

```js
// 开发插件 plugin.js
// Vue.js 的插件应该暴露一个 install 方法。这个方法的第一个参数是 Vue 构造器，第二个参数是一个可选的选项对象
export default {
  install: function (Vue, options) {
    Vue.myGlobalMethod = function () {} // 添加全局方法
    Vue.directive('my-directive', {}) // 添加全局资源
    Vue.mixin({}) // 注入组件选项
    Vue.prototype.$message = function () {} // 添加实例方法
  }
}

// 使用插件
// 通过全局方法 Vue.use() 使用插件。它需要在你调用 new Vue() 启动应用之前完成
import Vue from 'vue'
import plugin from './plugin.js'
Vue.use(plugin, options) // options 为可选的选项对象
```

---

# Vue

#### [vue-router](https://v3.router.vuejs.org/zh/)

<br />

> Vue.js 官方的路由管理器

<br />

- 注入

```js
// router 文件夹 index.js
import VueRouter from 'vue-router'
const router = new VueRouter({ routes }) // 创建 router 实例

// main.js 挂载 router
import Vue from 'vue'
import router from './router'
const app = new Vue({
  router
}).$mount('#app')
```

- 访问

```js
this.$router // 访问路由器
this.$route // 访问当前路由
```

---

# Vue

#### vue-router

<br />

- 模式：hash、history

```js
// 默认 hash，url 中包含 #
// history，url 中不包含 #
const router = new VueRouter({ mode: 'history', routes })
```

- 跳转

```js
// 声明式（标签跳转）
<router-link to=""></router-link>
<router-link to="" replace></router-link>

// 编程式（js跳转）
this.$router.push('/') // 向 history 栈添加一个新的记录
this.$router.replace('/') // 替换当前的 history 记录
this.$router.go(n) // 前进或后退 n 步
```

- router-view

```js
<router-view></router-view> // 渲染路径匹配到的视图组件
```

---

# Vue

#### vue-router

- 传参

```js
// query 参数 会在 url 后面拼接，变成 /register?plan=private
this.$router.push({ path: 'register', query: { plan: 'private' }}) // 传参
this.$route.query // 接收参数
// params 参数
this.$router.push({ name: 'register', params: { plan: 'private' }}) // 传参
this.$route.params // 接收参数
```

- routes

```js
routes: Array<RouteConfig>
interface RouteConfig = {
  path: string, // 路由路径
  component?: Component, // 组件
  name?: string, // 命名路由
  redirect?: string | Location | Function, // 重定向
  props?: boolean | Object | Function, // 路由参数
  alias?: string | Array<string>, // 别名
  children?: Array<RouteConfig>, // 嵌套路由
  meta?: any // 路由元信息 自定义路由配置
}
```

---

# Vue

#### vue-router

- 导航守卫

```js
// 全局守卫
// to: Route: 即将要进入的目标路由对象
// from: Route: 当前导航正要离开的路由
// next: Function: 一定要调用该方法来 resolve 这个钩子
// next() 进行管道中的下一个钩子 next(false) 中断当前的导航 next('/') 跳转到一个不同的地址
router.beforeEach((to, from, next) => { ... }) // 全局前置守卫

router.beforeResolve((to, from, next) => { ... }) // 全局解析守卫

router.afterEach((to, from) => { ... }) // 全局后置钩子

// 组件内的守卫（路由组件内，记录在路由表的组件）
beforeRouteEnter((to, from, next) => { ... }) // 在渲染该组件的对应路由被确认前调用

beforeRouteUpdate((to, from, next) => { ... }) // 在当前路由改变，但是该组件被复用时调用

beforeRouteLeave((to, from, next) => { ... }) // 导航离开该组件的对应路由时调用
```

---
layout: two-cols
---

# Vue

#### [Vuex](https://v3.vuex.vuejs.org/zh/)

<br />

> Vuex 是一个专为 Vue.js 应用程序开发的**状态管理**模式。vuex 更多地用于解决跨组件通信以及作为数据中心集中式存储数据

<br />

- 状态管理模式？

```js
new Vue({
  data () { // state 驱动应用的数据源
    return {
      count: 0
    }
  },
  template: `
    <div>{{ count }}</div>
  `, // view 以声明方式将 state 映射到视图
  methods: { // actions 响应在 view 上的用户输入导致的状态变化
    increment () {
      this.count++
    }
  }
})
```

:: right ::

<img src="/flow.png" />

<p style="font-size: 14px">我们期待以一种简单的“单向数据流”的方式管理应用，即状态 -> 视图 -> 操作单向循环的方式。但当我们的应用遇到多个组件共享状态时，单向数据流的简洁性很容易被破坏。因此，我们有必要把组件的共享状态抽取出来，以一个全局单例模式管理。通过定义和隔离状态管理中的各种概念并通过强制规则维持视图和状态间的独立性，我们的代码将会变得更结构化且易维护。</p>

---

# Vue

#### Vuex

<br />

- 注入

```js
// store 目录 index.js
import Vue from 'vue';
import Vuex from 'vuex';
import modules from './modules';

Vue.use(Vuex);
export default new Vuex.Store({ modules });

// main.js
import Vue from 'vue'
import store from './store'

new Vue({ store })
```

---
layout: two-cols
---

# Vue

#### Vuex

<br />

- 核心概念

| 核心概念 | 描述 |
| --- | --- |
| state | 单一数据源，存储应用状态 |
| getters | 对 state 进行计算操作 |
| mutations | 修改 state 的唯一途径， 只能是同步操作 |
| actions | 提交 mutation，可以包含任意异步操作 |
| modules | 模块 |

:: right ::

<div class="flex justify-center items-center h-100%">
  <img src="/vuex.png" />
</div>

---

# Vue

#### Vuex

<br />

- 使用

```js
// 直接调用 store
this.$store.state // state
this.$store.getters // getters
this.$store.commit('mutation handler', payload) // mutation payload 传入的参数，是一个对象
this.$store.dispatch('action handler', payload) // action payload 传入的参数，是一个对象
this.$store.dispatch({ type: 'action handler', ...payload  }) // action 对象形式调用

// 辅助函数
import { mapActions, mapMutations, mapState, mapGetters } from 'vuex'

computed: {
  ...mapState({ count: state => state.count }),
  ...mapGetters(['doneCount'])
},
methods: {
  ...mapMutations(['increment']),
  ...mapActions(['increment'])
}
```

---

# Vue

#### [Vue Loader](https://vue-loader.vuejs.org/zh/)

<br />

> Vue Loader 是一个 webpack 的 loader，它允许你以一种名为单文件组件 (SFCs)的格式撰写 Vue 组件

```js
<template>
  <div class="example">{{ msg }}</div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Hello world!'
    }
  }
}
</script>

<style> // lang scoped
.example {
  color: red;
}
</style>
```

---

# Vue

#### [Vue Devtools](https://chromewebstore.google.com/detail/nhdogjmejiglipccpnnnanhbledajbpd)

<br />

<img src="/devtools.png" />