<script>
import Vue from 'vue';
import IframeCp from '@/iframe-cp.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    IframeCp
  }
});
</script>

<template>
  <div id="app">
    <iframe-cp />
  </div>
</template>
