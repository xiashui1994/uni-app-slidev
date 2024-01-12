---
layout: two-cols
---

# 微信小程序

<br />

<div class="flex justify-center items-center absolute top-50% left-50% transform -translate-x-1/2 -translate-y-1/2">
  <img style="height: 200px" src="/mini-logo.jpg">
</div>

:: right ::

<br />

- 2017年1月9日小程序正式发布

- 快速的加载

- 更强大的能力

- 原生的体验

- 易用且安全的微信数据开放

- 高效和简单的开发

<br />

> 小程序是一种全新的连接用户与服务的方式，它可以在**微信**内被便捷地获取和传播，同时具有出色的使用体验

---

# 微信小程序

<br />

> 小程序与普通网页开发的区别

- 网页开发渲染线程和脚本线程是互斥的，小程序是分开的，分别运行在不同的线程中

- 小程序不存在跨域问题，但是请求地址需要在小程序后台配置

- 小程序开发只需要兼容 iOS 和 Android 的微信客户端，不用兼容 IE、Chrome、QQ 等浏览器

- 小程序可以调用微信能力，比网页开发功能更强大

- 小程序没有 DOM API 和 BOM API

- jQuery、Zepto 等一些 NPM 包在小程序中是无法运行的

- 小程序开发受制于微信的限制，没有网页开发自由

---

# 微信小程序

<br />

> 准备工作

- 申请账号：进入[小程序注册页](https://mp.weixin.qq.com/wxopen/waregister?action=step1)根据指引填写信息和提交相应的资料

- 获取 AppID：登录[小程序后台](https://mp.weixin.qq.com/)，我们可以在菜单 **开发** - **开发设置** 看到小程序的 AppID

- 安装开发工具：前往[开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html)下载页面 ，根据自己的操作系统下载对应的安装包进行安装

<br />

> 第一个小程序

<br />

- 打开开发者工具，新建项目选择小程序项目，选择代码存放的硬盘路径，填入小程序的 AppID
- 给你的项目起一个名字，勾选 "不使用云服务"，点击新建，你就得到了你的第一个小程序了

---
layout: two-cols
---

# 微信小程序

> 代码构成

- pages：页面
- utils：工具

- .json：JSON 配置文件

- .wxml：WXML 模板文件，类似 HTML

- .wxss：WXSS 样式文件，类似 CSS

- .js：JS 文件

> app.js 文件是小程序入口文件

:: right ::

<img src="/mini-code.png">

---
layout: two-cols
---

# 微信小程序

> 框架

- 渲染层的界面使用了 WebView 进行渲染

- 一个小程序存在多个界面，所以渲染层存在多个 WebView 线程

- 逻辑层采用 JsCore 线程运行 JS 脚本

- 通信会经由微信客户端做中转

- 逻辑层发送网络请求也经由微信客户端转发

> 缺点：大量修改数据会导致通信阻塞、创建多个 WebView 影响性能

:: right ::

<br />

<img src="/mini-main.png">

---

# 微信小程序

---

# 微信生态