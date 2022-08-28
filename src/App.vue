<script setup lang="ts">
import MultiLayer from "./components/MultiLayer/index.vue";
</script>

<template>
  <div id="app">
    <MultiLayer :pics="['public/0.png', 'public/1.png', 'public/2.png']" />
  </div>
</template>

<style scoped>
</style>
