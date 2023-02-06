<script>
export default /*#__PURE__*/ {
  name: "IframeCp", // vue component name
  props: {
    url: {
      type: String,
      default: "https://www.pudn.com/news/627e169c9b6e2b6d5541c74a.html",
    },
    iframeStyle: {
      type: String | Object,
      default: "min-height: 100vh; width: 100%",
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
