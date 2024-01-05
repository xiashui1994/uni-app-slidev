# 宿主环境

#### 什么是宿主环境

<br />

> JavaScript 宿主环境是指 JavaScript 代码运行的环境，它提供了访问和操作宿主环境中的功能和资源的能力

<br />

#### 常见宿主环境

- 浏览器
- Node.js
- Electron
- 移动应用
- 小程序

<br />

> JavaScript 宿主环境很多，所以需要对宿主环境进行适配

---

# 宿主环境

### 浏览器

<br />

| 内核 | 浏览器 |
| --- | --- |
| Trident | IE内核 |
| Gecko | Firefox |
| webkit | Safari |
| Chromium/Bink | Chrome/Edge |
| Presto | Opera |

<br />

> 国产浏览器都是基于 Chromium/Bink 内核魔改

---

# 宿主环境

### Node.js

<br />

> Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境，运行在服务器端，没有 DOM、BOM 和 window 对象

<br />

### Electron

<br />

> Electron 是一个基于 Chromium 和 Node.js 的桌面应用开发框架

<br />

### 移动应用

<br />

| 端 | 内核 |
| --- | --- |
| Android | Webview/X5/XWeb |
| iOS | WKWebView |

---

# 宿主环境

### 小程序

<br />

| 端 | 内核 |
| --- | --- |
| Android | 逻辑层 V8，视图层 XWeb |
| iOS | 逻辑层 JavaScriptCore，视图层 WKWebView |
| Windows | Chromium |
| MacOS | 逻辑层 JavaScriptCore，视图层 WKWebView |
| 开发者工具 | 逻辑层 NW.js，视图层 Chromium |
