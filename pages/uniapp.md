# uni-app

> uni-app 是一个使用 Vue.js 开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、Web（响应式）、以及各种小程序（微信/支付宝/百度/头条/飞书/QQ/快手/钉钉/淘宝）、快应用等多个平台

<br />

- 采用 vue 语法 + 微信小程序 api

- 通过条件编译 + 平台特有 API 调用，可以优雅的为某平台写个性化代码

- 一套代码，到处运行

- 文档丰富，通俗易懂

- 社区活跃，汉语环境

- 插件丰富，生态良好

---

# uni-app

<img src="/uni-function-diagram.png" style="height: 440px" />

---

# uni-app

> 基本语言

- js、vue、css 以及 ts、scss 等 css 预编译器

<br />

> 开发规范

- 页面文件遵循 Vue 单文件组件 (SFC) 规范，即每个页面是一个 .vue 文件

- 组件标签靠近小程序规范，详见 [uni-app 组件规范](https://uniapp.dcloud.net.cn/component/)

- 接口能力（JS API）靠近小程序规范，但需将前缀 wx、my 等替换为 uni，详见 [uni-app 接口规范](https://uniapp.dcloud.net.cn/api/)

- 数据绑定及事件处理同 Vue.js 规范，同时补充了[应用生命周期](https://uniapp.dcloud.net.cn/collocation/App.html#applifecycle)及[页面的生命周期](https://uniapp.dcloud.net.cn/tutorial/page.html#lifecycle)

---

# uni-app

> 组件

- 内置组件与小程序组件基本一致，不包含小程序新增的一些组件

- 扩展组件即 uni-ui 可以忽略，不推荐使用

- 使用组件时要看组件及对应属性的**平台差异说明**，不同平台不一致

<br />

> API

- API 与小程序 API 基本一致，不包含小程序新增的一些 API

- 使用 API 时要看 API 的**平台差异说明**，不同平台不一致

- web 平台可以操作DOM，支持 window、document、navigator 等浏览器的 API

---

# uni-app

#### [条件编译](https://uniapp.dcloud.net.cn/tutorial/platform.html)

<br />

> 条件编译是用特殊的注释作为标记，在编译时根据这些特殊的注释，将注释里面的代码编译到不同平台

<table style="font-size: 14px">
  <thead>
    <tr>
      <th>条件编译写法</th>
      <th>说明</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <div class="code">
          <span class="token comment"
            ><span style="color: #859900"> #ifdef</span
            ><b style="color: #268bd2"> APP-PLUS</b></span
          ><br />需条件编译的代码<br /><span class="token comment">
            <span style="color: #859900"> #endif</span></span
          >
        </div>
      </td>
      <td>仅出现在 App 平台下的代码</td>
    </tr>
    <tr>
      <td>
        <div class="code">
          <span class="token comment">
            <span style="color: #859900"> #ifndef</span
            ><b style="color: #268bd2"> H5</b></span
          ><br />需条件编译的代码<br /><span class="token comment">
            <span style="color: #859900"> #endif</span></span
          >
        </div>
      </td>
      <td>除了 H5 平台，其它平台均存在的代码（注意 if 后面有个 n）</td>
    </tr>
    <tr>
      <td>
        <div class="code">
          <span class="token comment">
            <span style="color: #859900"> #ifdef</span
            ><b style="color: #268bd2"> H5</b></span
          ><span style="color: #859900"> || </span
          ><b style="color: #268bd2">MP-WEIXIN</b
          ><br />需条件编译的代码<br /><span class="token comment">
            <span style="color: #859900"> #endif</span></span
          >
        </div>
      </td>
      <td>在 H5 平台或微信小程序平台存在的代码（这里只有 ||，不可能出现 &&，因为没有交集）</td>
    </tr>
  </tbody>
</table>

> 常用平台：APP：app端、H5：h5网页、MP-WEIXIN：微信小程序

---

# uni-app

#### 条件编译

<br />

> 注意

- 条件编译是利用注释实现的，在不同语法里注释写法不一样，js 使用 // 注释、css 使用 /* 注释 */、vue 模板里使用 \<!-- 注释 --\>

- 对于未定义平台名称，#ifdef 中的代码不会生效，而 #ifndef 中的代码会生效

- 使用条件编译请保证编译前和编译后文件的语法正确性，即要保障无论条件编译是否生效都能通过语法校验。比如：json 文件中不能有多余的逗号，js 中不能重复导入

<br />

> 条件编译还有更多用法，请参考[条件编译文档](https://uniapp.dcloud.net.cn/tutorial/platform.html)

---

# uni-app

#### 全局文件

<br />

> pages.json

pages.json 文件用来对 uni-app 进行全局配置，它类似微信小程序中 app.json 的页面配置部分，所有页面的配置都在这个文件

<br />

> manifest.json

manifest.json 文件是应用的配置文件，用于指定应用的名称、图标、权限等，小程序的一些配置也在这里

<br />

> App.vue

App.vue 是 uni-app 的主组件，类似于微信小程序中的 app.js

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