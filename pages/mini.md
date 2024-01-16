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

#### [程序注册](https://developers.weixin.qq.com/miniprogram/dev/reference/api/App.html)

<br />

> 每个小程序都需要在 app.js 中调用 App 方法注册小程序实例，绑定生命周期回调函数、错误监听和页面不存在监听函数等

```js
// app.js
App({
  onLaunch (options) {
    // 启动
  },
  onShow (options) {
    // 在前台展示
  },
  onHide () {
    // 在后台隐藏
  },
  onError (msg) {
    // 发生错误
  },
  globalData: 'I am global data' // getApp().globalData 获取全局数据
})
```

> [getApp](https://developers.weixin.qq.com/miniprogram/dev/reference/api/getApp.html)：获取到小程序全局唯一的 App 实例

---

# 微信小程序

#### [页面注册](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html)

<br />

> 对于小程序中的每个页面，都需要在页面对应的 js 文件中进行注册，指定页面的初始数据、生命周期回调、事件处理函数等

```js
// index.js
Page({
  data: {
    text: "This is page data."
  },
  onLoad: function(options) {}, // 页面创建时执行
  onShow: function() {}, // 页面出现在前台时执行
  onReady: function() {}, // 页面首次渲染完毕时执行
  onHide: function() {}, // 页面从前台变为后台时执行
  onUnload: function() {}, // 页面销毁时执行
  onPullDownRefresh: function() {}, // 触发下拉刷新时执行
  onReachBottom: function() {}, // 页面触底时执行
  onShareAppMessage: function () {}, // 页面被用户分享时执行
  onPageScroll: function() {}, // 页面滚动时执行
  ... // 业务相关方法
})
```

> [getCurrentPages](https://developers.weixin.qq.com/miniprogram/dev/reference/api/getCurrentPages.html)：获取当前页面栈。数组中第一个元素为首页，最后一个元素为当前页面

---

# 微信小程序

#### WXML

<br />

> WXML（WeiXin Markup Language）是框架设计的一套标签语言，结合基础组件、事件系统，可以构建出页面的结构

```html
<!-- 数据绑定 -->
<view> {{message}} </view>

<!-- 列表渲染 -->
<view wx:for="{{array}}"> {{item}} </view>

<!-- 条件渲染 -->
<view wx:if="{{view == 'WEBVIEW'}}"> WEBVIEW </view>
<view wx:elif="{{view == 'APP'}}"> APP </view>
<view wx:else="{{view == 'MINA'}}"> MINA </view>

<!-- <block/> 并不是一个组件，它仅仅是一个包装元素，不会在页面中做任何渲染，只接受控制属性 -->
<block wx:if="{{true}}">
  <view> view1 </view>
  <view> view2 </view>
</block>
```

> wxml 类似于 html，但 div、p 等标签在 wxml 中无效，只能写小程序组件（i 标签等文本样式标签有效，但不推荐使用）

---

# 微信小程序

#### WXSS

<br />

> WXSS (WeiXin Style Sheets)是一套样式语言，用于描述 WXML 的组件样式，WXSS 具有 CSS 大部分特性

<br />

- 尺寸单位

rpx（responsive pixel）: 可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。如在 iPhone6 上，屏幕宽度为375px，共有750个物理像素，则750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素

- 选择器

目前支持的选择器有：.class、#id、element、element, element、::after、::before

- 全局样式与局部样式

定义在 app.wxss 中的样式为全局样式，作用于每一个页面。在 page 的 wxss 文件中定义的样式为局部样式，只作用在对应的页面，并会覆盖 app.wxss 中相同的选择器

---

# 微信小程序

#### [WXS](https://developers.weixin.qq.com/miniprogram/dev/reference/wxs/)

<br />

> WXS（WeiXin Script）是内联在 WXML 中的脚本段。通过 WXS 可以在模版中内联少量处理脚本，丰富模板的数据预处理能力

```html
<!-- wxml -->
<wxs module="m1">
var msg = "hello world";

module.exports.message = msg;
</wxs>

<view> {{m1.message}} </view>
```

- WXS 是为了解决通信阻塞的问题引入的

- WXS 类似于有少量限制的 JavaScript，要完整了解 WXS 语法，请参考文档

- WXS 语法标准接近于 ES5

- WXS 也可以写在 .wxs 为后缀名的文件内，在 \<wxs\> 标签中引用

---

# 微信小程序

#### 事件

- 事件是视图层到逻辑层的通讯方式

- 事件可以将用户的行为反馈到逻辑层进行处理

- 事件可以绑定在组件上，当达到触发事件，就会执行逻辑层中对应的事件处理函数

- 事件对象可以携带额外信息，如 id，dataset，touches

```js
// wxml
<view id="tapTest" data-hi="Weixin" bindtap="tapName"> Click me! </view>

// js
Page({
  tapName: function(event) {
    console.log(event)
  }
})
```

> 调用事件不能直接传参，参数可以通过自定义属性 dataset 来传递

---

# 微信小程序

#### [事件分类](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/event.html#%E4%BA%8B%E4%BB%B6%E5%88%86%E7%B1%BB)

| 类型 | 触发条件
| --- | ---
| touchstart | 手指触摸动作开始
| touchmove | 手指触摸后移动
| touchcancel | 手指触摸动作被打断，如来电提醒，弹窗
| touchend | 手指触摸动作结束
| tap | 手指触摸后马上离开
| longpress | 手指触摸后，超过 350ms 离开，如果触发了这个事件，tap 事件将不被触发

<br />

> bind：绑定冒泡事件，catch：绑定非冒泡事件

---

# 微信小程序

#### 简易双向绑定

<br />

> 在 WXML 中，普通的属性的绑定是单向的

```html
<!-- 使用 this.setData({ value: 'leaf' }) 来更新 value -->
<input value="{{value}}" />

<!-- 输入框的值被改变了， this.data.value 也会同时改变 -->
<input model:value="{{value}}" />
```

<br />

- 小程序中的双向绑定是通过 setData 来更新属性的值，而不是直接修改属性的值，类似于 React

<br />

> Page.prototype.setData 函数用于将数据从逻辑层发送到视图层（异步），同时改变对应的 this.data 的值（同步）

---

# 微信小程序

#### [全局配置](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html)

<br />

> 小程序根目录下的 app.json 文件用来对微信小程序进行全局配置

```json
{
  "pages": [ // 小程序中新增/减少页面，都需要对 pages 数组进行修改
    "pages/index/index" // 未指定 entryPagePath 时，数组的第一项代表小程序的初始页面（首页）
  ],
  "window": { // 用于设置小程序的状态栏、导航条、标题、窗口背景色
    "navigationBarTitleText": "Demo" // 导航栏标题文字内容	
  },
  "tabBar": { // 配置 tabbar
    "list": [{ // tabbar 列表
      "pagePath": "pages/index/index", // 页面路径，必须在 pages 中先定义
      "text": "首页" // tab 上按钮文字
    }]
  },
  "networkTimeout": { // 各类网络请求的超时时间，单位均为毫秒
    "request": 10000 // request 超时时间
  }
}
```

---

# 微信小程序

#### [页面配置](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/page.html)

<br />

> 可以使用同名 .json 文件来对本页面的窗口表现进行配置，页面中配置项会覆盖 app.json 的 window 中相同的配置项

```json
{
  "navigationBarBackgroundColor": "#ffffff", // 导航栏背景颜色
  "navigationBarTextStyle": "black", // 导航栏标题、状态栏颜色，仅支持 black / white
  "navigationBarTitleText": "微信接口功能演示", // 导航栏标题文字内容	
  "backgroundColor": "#eeeeee", // 窗口的背景色
  "backgroundTextStyle": "light", // 下拉 loading 的样式，仅支持 dark / light
  "navigationStyle": "default", // 导航栏样式，default 默认样式 custom 自定义导航栏
  "enablePullDownRefresh": true, // 开启下拉刷新
  "onReachBottomDistance": 50, // 页面上拉触底距离，单位为 px
  "disableScroll": true, // 禁止页面滚动
  "usingComponents": {
    "swiper": "/components/swiper/swiper" // 自定义组件
  }
}
```

---
layout: two-cols
---

# 微信小程序

#### [自定义组件](https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/)

<br />

> 开发者可以将页面内的功能模块抽象成自定义组件，以便在不同的页面中重复使用，类似于页面，一个自定义组件由 json wxml wxss js 4个文件组成

<br />

- json

```json
{
  "component": true // 将这一组文件设为自定义组件
}
```

- wxml

```html
<view class="wrapper">
  <!-- 承载组件引用时提供的子节点 -->
  <slot></slot>
  <!-- 在组件定义时的选项中启用多slot支持，以不同的 name 来区分 -->
  <slot name="before"></slot>
</view>
```

:: right ::

- wxss

```css
/* 组件对应 wxss 文件的样式，只对组件wxml内的节点生效 */

#a { } /* 在组件中不能使用 */
[a] { } /* 在组件中不能使用 */
button { } /* 在组件中不能使用 */
.a > .b { } /* 除非 .a 是 view 组件节点，否则不一定会生效 */
```

- js

```js
Component({
  options: {
    multipleSlots: true, // 在组件定义时的选项中启用多slot支持
    styleIsolation: 'isolated' // 指定特殊的样式隔离选项
    // isolated 表示启用样式隔离
    // apply-shared 表示页面 wxss 样式将影响到自定义组件，但自定义组件 wxss 中指定的样式不会影响页面
    // shared 表示页面 wxss 样式将影响到自定义组件，自定义组件 wxss 中指定的样式也会影响页面和其他设置了
  },
  externalClasses: ['my-class'], // 外部样式类
  data: {}, // 私有数据，可用于模板渲染
  methods: {}, // 组件方法
  properties: {}, // 组件的对外属性，是属性名到属性设置的映射表
  observers: {}, // 组件数据字段监听器，用于监听 properties 和 data 的变化
  behaviors: [] // 类似于 mixins 的组件间代码复用机制
})
```

---

# 微信小程序

#### 自定义组件

- 组件生命周期

```js
Component({
  // 生命周期函数，可以为函数，或一个在 methods 段中定义的方法名
  lifetimes: {
    created: function () {}, // 在组件实例刚刚被创建时执行
    attached: function () {}, // 在组件实例进入页面节点树时执行
    ready: function () {}, // 在组件在视图层布局完成后执行
    moved: function () {}, // 在组件实例被移动到节点树另一个位置时执行
    detached: function () {}, // 在组件实例被从页面节点树移除时执行
    error: function () {} // 每当组件方法抛出错误时执行
  },
  // 组件所在页面的生命周期函数
  pageLifetimes: {
    show: function () {}, // 组件所在的页面被展示时执行
    hide: function () {}, // 组件所在的页面被隐藏时执行
    resize: function () {} // 组件所在的页面尺寸变化时执行
  }

  // 旧式的定义方式
  created () {}, attached () {}, ready () {}, moved () {}, detached () {}
})
```

---
layout: two-cols
---

# 微信小程序

#### 自定义组件

- 组件间通信

```js
// 页面
<component prop-a="{{a}}" bindmyevent="onMyEvent" />
Page({
  onMyEvent: function(e){
    e.detail // 自定义组件触发事件时提供的detail对象
  }
})

// 组件
<button bindtap="onTap">点击这个按钮将触发“myevent”事件</button>
Component({
  properties: { propA: String },
  methods: {
    onTap: function(){
      var myEventDetail = {} // detail对象，提供给事件监听函数
      var myEventOption = {} // 触发事件的选项 bubbles 事件是否冒泡 composed 事件是否可以穿越组件边界 capturePhase 事件是否拥有捕获阶段
      this.triggerEvent('myevent', myEventDetail, myEventOption)
    }
  }
})
```

:: right ::

- 使用组件

```json
{
  // 在页面配置中引入组件
  "usingComponents": {
    "swiper": "/components/swiper/swiper" // 自定义组件
  }
}
```

---
layout: two-cols
---

# 微信小程序

#### [组件](https://developers.weixin.qq.com/miniprogram/dev/component/)

<br />

> 视图容器

- view：视图容器

- scroll-view：可滚动视图区域

- swiper：滑块视图容器

- swiper-item：仅可放置在 swiper 组件

- cover-view：覆盖在原生组件之上的文本视图

- cover-image：覆盖在原生组件之上的图片视图

> 小程序中的 camera、canvas、input、video、textarea 等组件是由客户端创建的原生组件，目前原生组件均已支持**同层渲染**

:: right ::

> 基础内容

- text：文本

- rich-text：富文本

<br />

> 表单组件

- button：按钮

- input：输入框

- textarea：多行输入框

> button 在小程序中不仅仅是按钮，附带了很多功能，如：获取用户的手机号码、获取用户的头像、获取用户的昵称等，由 open-type 属性决定

---
layout: two-cols
---

# 微信小程序

#### 组件

<br />

> 媒体组件

- audio：音频

- camera：系统相机

- image：图片

- video：视频

<br />

> 画布

- canvas：画布

:: right ::

> 开放能力

- ad：广告

- web-view：承载网页的容器

> web-view 会自动铺满整个小程序页面，**个人类型的小程序暂不支持使用**

---
layout: two-cols
---

# 微信小程序

#### [API](https://developers.weixin.qq.com/miniprogram/dev/api/)

<br />

> 基础

- wx.canIUse：检查小程序的 API 接口是否支持

- wx.getWindowInfo：获取窗口信息

- wx.getSystemInfo：获取系统信息

- wx.getDeviceInfo：获取设备信息

- wx.getUpdateManager：获取版本更新管理器

- wx.updateWeChatApp：更新微信客户端

> 小程序的[基础库](https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/)会随着微信一起更新，可能更新/删除/限制/放开某个 API，所以尽可能使用稳定的 API，canIUse 尽可能少用

:: right ::

> 路由

- wx.switchTab：跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面

- wx.reLaunch：关闭所有页面，打开到应用内的某个页面

- wx.redirectTo：关闭当前页面，跳转到应用内的某个页面。但是不允许跳转到 tabbar 页面

- wx.navigateTo：保留当前页面，跳转到应用内的某个页面。但是不能跳到 tabbar 页面

- wx.navigateBack：关闭当前页面，返回上一页面或多级页面

- EventChannel：页面间事件通信通道

> 小程序中页面栈最多**十层**，需要注意页面栈的深度

---
layout: two-cols
---

# 微信小程序

#### API

<br />

> 跳转

- wx.openEmbeddedMiniProgram：打开半屏小程序

- wx.navigateToMiniProgram：打开另一个小程序

<br />

> 转发

- wx.showShareMenu：显示当前页面的转发按钮

- wx.hideShareMenu：隐藏当前页面的转发按钮

:: right ::

> 界面

- wx.showToast：显示消息提示框

- wx.showModal：显示模态框

- wx.showLoading：显示 loading 提示框

- wx.showActionSheet：显示操作菜单

- wx.hideToast：隐藏消息提示框

- wx.hideLoading：隐藏 loading 提示框

- wx.setNavigationBarTitle：动态设置当前页面的标题

- wx.hideHomeButton：隐藏返回首页按钮

- wx.showTabBar：显示 tabBar

- wx.hideTabBar：隐藏 tabBar

---
layout: two-cols
---

# 微信小程序

#### API

<br />

> 界面

- wx.pageScrollTo：将页面滚动到目标位置

- wx.getMenuButtonBoundingClientRect：获取菜单按钮（右上角胶囊按钮）的布局位置信息

<br />

> 网络

- wx.request：发起 HTTPS 网络请求

- wx.downloadFile：下载文件资源到本地

- wx.uploadFile：将本地资源上传到服务器

:: right ::

> 支付

- wx.requestPayment：发起支付

<br />

> 数据缓存

- wx.setStorage：将数据存储在本地缓存指定的 key 中

- wx.removeStorage：移除本地缓存中指定的 key

- wx.getStorage：获取本地缓存中指定的 key

- wx.clearStorage：清理本地缓存

> 数据缓存中的 API 有同步版本，可以根据情况使用，单个 key 允许存储的最大数据长度为 1MB，所有数据存储上限为 10MB


---
layout: two-cols
---

# 微信小程序

#### API

<br />

> 画布

- wx.createCanvasContext：创建 canvas 的绘图上下文

- wx.canvasToTempFilePath：把当前画布指定区域的内容导出生成指定大小的图片

<br />

> 媒体

- wx.previewMedia：预览图片和视频

- wx.previewImage：在新页面中全屏预览图片

- wx.compressImage：压缩图片

:: right ::

- wx.chooseImage：从本地相册选择图片或使用相机拍照

- wx.createVideoContext：创建 video 上下文

- wx.compressVideo：压缩视频

- wx.chooseMedia：拍摄或从手机相册中选择图片或视频

- wx.createInnerAudioContext：创建内部 audio 上下文

- wx.createCameraContext：创建 camera 上下文


---
layout: two-cols
---

# 微信小程序

#### API

<br />

> 文件

- wx.openDocument：新开页面打开文档

- wx.getFileSystemManager：获取全局唯一的文件管理器

<br />

> 开放接口

- wx.login：调用接口获取登录凭证

- wx.openSetting：调起客户端小程序设置界面

- wx.openCustomerServiceChat：打开微信客服

:: right ::

> 设备

- wx.setClipboardData：设置系统剪贴板的内容

- wx.getClipboardData：获取系统剪贴板的内容

- wx.getNetworkType：获取网络类型

- wx.makePhoneCall：拨打电话

- wx.vibrateShort：使手机发生较短时间的振动（15 ms）

<br />

> WXML

- wx.createSelectorQuery：返回一个 SelectorQuery 对象实例

<br />

> 类似于 boundingClientRect 获取的节点位置信息

---

# 微信小程序

#### [开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/devtools.html)

<br />

> 推荐使用 VsCode 开发，开发者工具只预览发布小程序

<br />

<img src="/mini-tools.png" style="height: 320px" />

---

# 微信小程序

#### 开发者工具

<br />

<div class="flex justify-center items-center">
  <img src="/tools.png" style="height: 320px" />
  <img src="/wxml.png" style="height: 320px" />
</div>

---

# 微信小程序

#### 发布小程序

<br />

> 一个小程序从开发完到上线一般要经过 **预览 -> 上传代码 -> 提交审核 -> 发布** 等步骤

<br />

- 预览

点击开发者工具顶部操作栏的**预览**按钮，使用当前小程序开发者的微信扫码即可看到小程序在手机客户端上的真实表现

- 上传代码

点击开发者工具顶部操作栏的**上传**按钮，填写版本号以及项目备注等，上传成功之后，登录**小程序管理后台 - 版本管理 - 开发版本** 就可以找到提交上传的版本

- 提交审核

在开发版本的列表中，点击 **提交审核** 按照页面提示，填写相关的信息，即可将小程序提交审核

---

# 微信小程序

#### 发布小程序

<br />

- 发布

审核通过之后，管理员及提交审核的微信中会收到小程序通过审核的通知，此时登录 **小程序管理后台 - 版本管理 - 审核版本** 中可以看到通过审核的版本，点击**发布**后，即可发布小程序

> 可以在微信中搜索 **小程序助手**，管理发布小程序更方便

---

# 微信小程序

#### 小程序的版本

<br />

> 小程序没有开发、灰度、线上等环境概念，只有版本区分

| 版本 | 权限 | 说明 |
| ---- | ---- | ---- |
| 开发版本 | 开发者 | 使用开发者工具上传的代码 |
| 体验版本 | 体验成员 | 可以选择某个开发版本作为体验版 |
| 审核中版本 | 开发者 | 审核中的代码，可直接重新提交审核，覆盖原审核版本 |
| 线上版本 | 所有用户 | 线上所有用户使用的代码版本，该版本代码在新版本代码发布后被覆盖更新 |

<br />

> 项目中可以开发时用开发环境体验版，测试通过后，上传正式环境体验版提交审核并发布

---

# 微信生态

> 微信自 2011年1月21日 至今，已经成长为类操作系统的 APP，包含 公众号、小程序、视频号 等，是一个巨大的流量入口，想要为产品引流，微信生态是必然选择

<br />

- openId

当前小程序、公众号的**用户唯一标识**

- unionId

同一个**微信开放平台**账号下的移动应用、网站应用和公众账号（包括小程序），用户的 unionId 是唯一的

- 微信打开公众号

订阅号消息、订阅通知、搜索、聊天卡片、海报二维码、公众号链接等

- 微信打开小程序

下拉菜单、搜索、小程序通知、小程序卡片、海报二维码、小程序码、小程序链接等

---

# 微信生态

- 小程序跳转公众号

webview、公众号关注组件

- 公众号跳转小程序

公众号菜单、公众号消息、公众号通知、公众号文章
