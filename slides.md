---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: 2024 CSS Trend
info: |
  ## 2024 CSS Trend
  Fuck off JS
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# take snapshot for each slide in the overview
overviewSnapshots: true
---

# 2024 CSS Trend

### Fuck off JS

<style>
  h3{
    opacity: 0.7
  }
</style>

---

# Before We Start

<div class='container'>
 Uninstall your FireFox 
</div>

<style>
  .container{
    width: 100%;
    height: 80%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 40px;
  }
</style>

---

# `:has` Selector

#### The parent selector can determine the style of the parent based on its children.

<p>Since December 2023, this feature works across the latest devices and browser versions. This feature might not work in older devices or browsers.</p>

````md magic-move {lines: true}
<!-- step 1 -->

```html
<div class="parent">
  <div class="child"></div>
</div>
```

<!-- step 2 -->

```css
.parent:has(.child) {
  /* css 代碼 */
}
```

<!-- step 3 -->

```css
button:has(.icon) {
  display: flex;
  gap: 10px;
}
```

<!-- step 4 -->

```css
/* pass css when card has image with sibling p  */
.card:has(img + p) {
  flex-direction: column;
}
```

<!-- step 5 -->

```css
.card:not(:has(img)) {
  /* css for card without img element  */
}
```

<!-- step 6 -->

```css
/* pass css by children's condition  */
form:has(input:invalid) {
  border: 1px solid red;
}
```

<!-- step 8 -->

```html
<!-- Make a previous sibling selector -->
<div>
  <div>我是前一個元素</div>
  <p>我是當前元素</p>
</div>
```

<!-- step 8 -->

```css
/* Make a previous sibling selector  */
div:has(+ p) {
  color: red;
}

div + p {
  font-size: 20px;
}
```
````

<Sibling v-click='7'/>

<style>
  p{
    opacity: 0.5
  }
</style>

<!--
父層選擇器，可以根據子代去決定父層的樣式

- 按鈕包含圖示的話則讓按鈕跟文字間隔 10px
- 卡片內有圖片和文字相鄰，讓他們縱向排列
- 可以結合 :not 去設定進一步的條件
- 透過 child 的狀態去給定樣式


以前我可以透過 + 來選擇後一個元素，有了 : has，可以配合 + 來選擇前一個元素
-->

---

# Advanced Uses of `:has` Selector

```css {*|1-3|5-7|9-11}{lines:true}
ul:has(> :nth-child(5)) {
  outline: 1px solid green;
}

ul:has(> :nth-child(5):last-child) {
  outline: 1px solid blue;
}

ul:not(:has(> :nth-child(5))) {
  outline: 1px solid red;
}
```

<ListCounter :count="1" m="t-4"/>

---

# Anywhere Selector

```css {*}{lines:true}
.container:has(option[value="dark"]:checked) {
  --primary-color: #e43;
  --surface-color: #1b1b1b;
  --text-color: #eee;
}
```

<ThemeSelector />

<!--
使用更高層級的元素，甚至可以跨多個層級去決定其他地方的樣式
-->

---

# Container Queries - Size

`Container Queries` allows styles to be applied based on the size of the container, enabling components to determine their styles based on their own dimensions rather than relying on the window size.

<div class="containerQueryDesc">
  <ul>
    <li>No longer constrained by the viewport, you can better predict how components will render</li>
    <li>This also improves reusability, ensuring consistent style application logic regardless of which page the component is placed on</li>
    <li>A revolutionary new CSS length property</li>
  </ul>
  <img width="40%"  src="https://web.dev/static/blog/cq-stable/image/media-queries-vs-containe-fa94919e025e3.png?hl=zh-tw"/>
</div>

<style>
  .containerQueryDesc{
    display: flex;
  }
</style>

<!--
允許透過容器的尺寸來套用樣式，元件可以根據
自身的大小判斷樣式而不用依賴於視窗

- 不用再看 viewport 眼色，更好的預期元件會 是怎麼呈現
- 更好的重用性，不論放到哪個頁面都會是一致 的樣式套用邏輯
- 嶄新的 css length 屬性
-->

---

# Container Queries - Code

```html {*}{lines:true}
<div class="element-wrap">
  <div class="element"></div>
</div>
```

```css {*}{lines:true}
.element-wrap {
  /* container-name: element; */
  /* container-type: inline-size; */
  /* shorthand: name / type */
  container: element / inline-size;
}
@container element (min-inline-size: 300px) {
  .element {
    display: flex;
    gap: 1rem;
  }
}
```

---

# Container Queries - Demo

<ContainerQuery />

---

# Scroll-Driven Animations

<AnimationTimelineScroll />

---

# Scroll-Driven Animations - Code

````md magic-move {lines: true}
```html{*|1,2}
<div class="timeline-scroll-container">
    <div class="progress"></div>
      <div class="container">
        <!-- some contain ...  -->
      </div>
    </div>
</div>
```

```css{*|1,10,11,12,23}
@keyframes progress {
  from {
    transform: scaleX(0);
  }
  to {
    transform: scaleX(1);
  }
}

.timeline-scroll-container {
  scroll-timeline: --progress block;
}

.progress {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 0.5rem;
  background-color: #f08080;
  transform-origin: 0 50%;
  animation: progress auto linear;
  animation-timeline: --progress;
}
```
````

---

# Anchor Position

### Typically, to position one element relative to another, one of the elements must be a descendant of the other.

### Now, even if they are not in a parent-child relationship, it’s no longer an issue!

<div class="anchor-wrapper">

```html{*}{lines: true}
<div class="tooltip tooltip-1">I'm an anchored tooltip.</div>
<div class="tooltip tooltip-2">Me too!</div>
<div class="el">Just Some Element</div>

<style>
.el {
  anchor-name: --my-anchor;
}
.tooltip-1 {
  bottom: anchor(--my-anchor top);
  left: anchor(--my-anchor center);
}
.tooltip-2 {
  top: anchor(--my-anchor center);
  left: anchor(--my-anchor right);
}
</style>
```

  <AnchorName />
</div>

<style>
  .anchor-wrapper{
    display: flex;
    gap: 20px;
    margin-top: 20px;
    padding: 0 40px;
  }
  .slidev-code-wrapper{
    flex-grow: 3;
  }
  .anchor-name-container{
    flex-grow: 2;
    margin-top: 80px;
  }
</style>

<!--
通常我們要讓一個元素依附在另外一個元素上的相對位
置，其中一個元素必定為另一個元素的子代
現在即便不是子代也沒有關係
-->

---

# Justify-self

You can use justify-self with block elements to center them without using Flexbox or CSS Grid. A good replacement for margin: auto (combined with width).

⚠️ Chrome only for now ⚠️

<div class="justify-self-container">
```css
.justify-self {
  justify-self: center;
}
```
  <div class="justify-self-wrapper">
    <div class="justify-self">justify-self</div>
  </div>
</div>

<style>
  .justify-self-container{
    display: flex;
    gap: 20px;
    margin-top: 20px;
    padding: 0 40px;
  }
  .slidev-code-wrapper{
    flex-grow: 1;
  }
  .justify-self-wrapper{
    width: 400px;
    height: 50px;
    border: 1px solid #FFF;
    box-sizing: border-box;
  }
  .justify-self{
    justify-self: center;
    height: 48px;
    border: 1px solid #ccc;
    box-sizing: border-box;
    border-radius: 4px;
    padding: 5px;
  }
</style>

---

<div class="thank-you">
  <h1>Thank You For your Attention</h1>
</div>

<style>
  .thank-you{
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
