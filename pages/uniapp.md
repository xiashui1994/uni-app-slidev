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

App.vue 是 uni-app 的主组件，类似于微信小程序中的 app.js，不能写 \<template\>

---

# uni-app

#### 插件

<br />

> [插件市场](https://ext.dcloud.net.cn/)

uni-app 插件市场，是 uni-app 官方插件生态集中地。不过开发者水平参差不齐，要仔细甄别，还要考虑插件的兼容平台

> [uni_modules](https://uniapp.dcloud.net.cn/plugin/uni_modules.html)

uni_modules 是 uni-app 的插件模块化规范，通常是对一组 js sdk、组件、页面、uniCloud云函数、公共模块等的封装，用于嵌入到 uni-app 项目中使用，也支持直接封装为项目模板

> [easycom](https://uniapp.dcloud.net.cn/component/#easycom)

easycom 可以不用引用、注册组件，直接在页面中使用，只要组件安装在项目的 components 目录下或 uni_modules 目录下，并符合 **components/组件名称/组件名称.vue** 目录结构。如果你的组件名称或路径不符合 easycom 的默认规范，可以在 **pages.json** 的 easycom 节点进行个性化设置，自定义匹配组件的策略

---

# uni-app

#### [uView UI](https://uviewui.com/)

<br />

> uView UI，是全面兼容 uni-app 生态的框架，全面的组件和便捷的工具会让您信手拈来，如鱼得水

- 组件：覆盖开发过程的各个需求，功能丰富，多端兼容

- API：内置常用工具函数，能够满足大部分需求，挂载在 **uni.$u** 对象上

#### [uCharts](https://www.ucharts.cn/v2/#/)

<br />

> uCharts 是一款基于 canvas API 开发的适用于所有前端应用的图表库

- [原生方式](https://www.ucharts.cn/v2/#/doc/index)

- [组件方式](https://www.ucharts.cn/v2/#/tool/index)（项目使用方式）

---
layout: two-cols
---

# uni-app

#### 框架

<br />

```bash
├─.editorconfig                 // 编辑器配置
├─.eslintignore                 // eslint忽略文件
├─.eslintrc.js                  // eslint配置
├─.gitignore                    // git忽略文件
├─README.md                     // 说明文档
├─babel.config.js               // babel配置
├─package-lock.json             // npm版本控制
├─package.json                  // 包管理
├─postcss.config.js             // postcss配置
├─tsconfig.json                 // ts配置        
├─vue.config.js                 // vue配置
├─src                           // 资源目录
├─public                        // 模板目录
|   └index.html                 // h5模板
```

> uni-app 开发框架基于 vue-cli 创建

:: right ::

<br />

```bash
├─src                           // 资源目录
|  ├─App.vue                    // 页面入口文件
|  ├─main.js                    // 项目入口文件
|  ├─manifest.json              // 应用配置文件
|  ├─pages.json                 // 全局页面配置
|  ├─uni.scss                   // 预置scss变量
|  ├─utils                      // 工具库
|  |   └util.js                 // 函数工具库
|  ├─static                     // 静态资源
|  ├─plugins                    // 拓展插件
|  |    ├─luch-request          // 跨平台请求插件
|  |    |      └config.js       // 插件配置
|  ├─pages                      // 页面目录
|  |   ├─index                  // 首页示例
|  |   |   └index.vue
|  ├─feConfig                   // 环境配置
|  |    ├─development.js        // 开发环境
|  |    ├─production.js         // 生产环境
|  |    └test.js                // 测试环境
|  ├─constants                  // 常量
|  |    └enum.js                // 枚举文件
```

---
layout: two-cols
---

# uni-app

#### 运行、发布

- 开发：`npm run dev:%PLATFORM%`

- 测试：`npm run test:%PLATFORM%`

- 正式：`npm run build:%PLATFORM%`

- 发布：打包后的产物在 `dist/build/%PLATFORM%` 目录

<br />

> %PLATFORM%: h5、mp-weixin 等

:: right ::

<div class="flex items-center justify-center h-full">
  <img src="/build.png" />
</div>

---
layout: end
---

Thank you