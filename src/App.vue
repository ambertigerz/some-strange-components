<script setup lang="ts">
import MultiLayer from "./components/MultiLayer/index.vue";
</script>

<template>
  <div id="app">
    <div style="width: 500px; height: 400px">
      <MultiLayer :pics="[{ layerSrc: '/0.png' }, { layerSrc: '/1.png' }, { layerSrc: '/2.png' }]" />
    </div>
  </div>
</template>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>