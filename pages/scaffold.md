# 前端开发框架（脚手架）

#### 定位

<br />

> 快速的搭建项目的**基本结构**并提供项目**规范和约定**

<br />

#### 发展历程

<br />

> 模块化、工程化、智能化

<br />

#### 解决的问题

- 提高开发生产效率

- 制定开发规范，提高团队协作能力

- 预编译，包括es6/7语法转译、css预编译器处理

- 文件压缩、依赖打包

---
layout: two-cols
---

#### Vue 脚手架

<br />

> [webpack](https://webpack.js.org/)

<br />

<img style="width: 200px;" src="/webpack.png" />

<br />

> 特征：有 webpack.conf.js 配置文件

:: right ::

> [vue-cli](https://cli.vuejs.org/)

<br />

<img style="width: 200px;" src="/vue-cli.png" />

<br />

> 特征：有 vue.config.js 配置文件

---
layout: two-cols
---

#### Vue 脚手架

<br />

> [Vite](https://cn.vitejs.dev/)

<br />

<img style="width: 200px;" src="/vite.png" />

<br />

> 特征：有 vite.config.ts 配置文件

:: right ::

#### [npm](https://www.npmjs.com/)

<br />

> npm 是 Node.js 的包管理工具

<br />

- [package.json](https://juejin.cn/post/7240805459288522808)：包管理配置文件

- 使用

```bash
npm install / i <package_name> // 安装依赖
npm uninstall <package_name> // 卸载依赖

// 参数
-S, --save // 保存生产依赖 记录在 dependencies 中
-D, --save-dev // 保存开发依赖 记录在 devDependencies 中
-g // 安装全局依赖

```

<br />

- 包管理工具：[pnpm](https://pnpm.io/zh/)、[npm](https://www.npmjs.com/)、[yarn](https://github.com/yarnpkg/yarn)

---
layout: two-cols
---

#### Vue 脚手架

<br />

> 相关配置

- [editorConfig](https://editorconfig.org/)：编辑器配置

- [eslint](https://eslint.org/)：代码规范

- [babel](https://babeljs.io/)：代码转换

- [postcss](https://postcss.org/)：css 预处理

- [styleLint](https://stylelint.io/)：css 规范

- [husky](https://github.com/typicode/husky)：commit 钩子

- [commitlint](https://github.com/conventional-changelog/commitlint)：commit 规范

:: right ::

> 相关依赖

- 组件库：[element-ui](https://element.eleme.cn/)、[uview-ui](https://uviewui.com/)

- 请求库：[axios](https://axios-http.com/)、[luch-request](https://www.quanzhan.co/luch-request)、[uni-ajax](https://uniajax.ponjs.com/)

- 图表库：[echarts](https://echarts.apache.org/)、[uCharts](https://www.ucharts.cn/v2/#/)

- 时间处理：[moment](https://momentjs.com/)、[dayjs](https://dayjs.gitee.io/zh-CN/)

- CSS 预处理：[sass](https://sass-lang.com/)、[less](https://lesscss.org/)

- 环境变量：[cross-env](https://github.com/kentcdodds/cross-env)

- 自动导入：[unplugin-auto-import](https://github.com/antfu/unplugin-auto-import)

- 单元测试：[vitest](https://vitest.dev/)、[karma](https://karma-runner.github.io/)、[jest](https://jestjs.io/)
