---
title: 跳转别人的页面，怎么加个返回呢
tags: vue
categories: vue
theme: vue-pro
highlight:
---

有时候需要跳转别人的页面，但是需要在别人的页面，加个返回之类等，我们需要的逻辑。
此时，`iframe`就是个不错的解决方案
但是 `iframe` 的属性，我总记不住，索性写个组件，回头就可以直接用了

## 安装

```shell
# yarn add iframe-cp
npm i iframe-cp
```

## 使用

```js
import IframeCp from 'iframe-cp';

<iframe-cp url="https://www.pudn.com/news/627e169c9b6e2b6d5541c74a.html">
  写返回键之类巴拉巴拉的
</iframe-cp>;
```

`iframe`需要特定样式的话，直接传入`iframeStyle="...."`就好

## 案例

```vue
<template>
  <iframe-cp url="https://www.pudn.com/news/627e169c9b6e2b6d5541c74a.html">
    <div class="header" @click="() => this.$router.go(-1)">
      <img
        width="24"
        src="https://blog-huahua.oss-cn-beijing.aliyuncs.com/blog/code/back.png"
        alt=""
        class="icon"
      />
    </div>
  </iframe-cp>
</template>
<style scoped>
.header {
  height: 44px;
  display: flex;
  background: #fff;
  align-items: center;
  padding-left: 16px;
  padding-right: 16px;
}
</style>
```

[案例效果](https://blog-huahua.oss-cn-beijing.aliyuncs.com/blog/code/back_iframe.png)

## 原理

没啥原理，就是`iframe`，属性是

```html
<iframe :src="url" frameborder="0" :style="iframeStyle"></iframe>
```

## 源码

```vue
<script>
export default /*#__PURE__*/ {
  name: 'IframeCp', // vue component name
  props: {
    url: {
      type: String,
      default: 'https://www.pudn.com/news/627e169c9b6e2b6d5541c74a.html',
    },
    iframeStyle: {
      type: String | Object,
      default: 'min-height: 100vh; width: 100%',
    },
  },
};
</script>

<template>
  <div class="iframe-cp">
    <slot> </slot>
    <iframe :src="url" frameborder="0" :style="iframeStyle"></iframe>
    <slot name="after"> </slot>
  </div>
</template>
```
