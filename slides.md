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
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# 目录

<div class="font-bold cursor-pointer">
  <div class="mb-4" @click="$slidev.nav.go(4)">1. HTML</div>
  <div class="mb-4" @click="$slidev.nav.go(6)">2. CSS</div>
  <div class="mb-4" @click="$slidev.nav.go(36)">3. JavaScript</div>
  <div class="mb-4" @click="$slidev.nav.go(68)">4. 宿主环境</div>
  <div class="mb-4" @click="$slidev.nav.go(72)">5. Vue</div>
  <div class="mb-4" @click="$slidev.nav.go(106)">6. 前端开发框架</div>
  <div class="mb-4" @click="$slidev.nav.go(110)">7. 微信小程序</div>
  <div class="mb-4" @click="$slidev.nav.go(142)">8. uni-app</div>
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
src: ./pages/html.md
---

---
src: ./pages/css.md
---

---
src: ./pages/js.md
---

---
src: ./pages/host.md
---

---
src: ./pages/vue.md
---

---
src: ./pages/scaffold.md
---

---
src: ./pages/mini.md
---

---
src: ./pages/uniapp.md
---
