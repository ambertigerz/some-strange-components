<script setup lang="ts">
import { ref } from "vue";

interface iMultiLayer {
  pics: Array<string>;
  width?: number | string;
  height?: number | string;
}

withDefaults(defineProps<iMultiLayer>(), {
  width: "100%",
  height: "100%",
});
</script>

<template>
  <div id="multi-layer-container">
    <img
      v-for="(i, index) in pics"
      :key="index"
      :src="i"
      :alt="index + ''"
      :style="{ zIndex: 50 - index, position: 'absolute', right: 0, left: 0 }"
    />
  </div>
</template>

<style scoped>
#multi-layer-container {
  display: flex;
  position: relative;
  box-sizing: border-box;
  width: v-bind(width);
  height: v-bind(height);
}
</style>
