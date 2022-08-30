<template>
  <div id="multi-layer-container" @mousemove="mouseMove" @mouseleave="() => { left = 50 }" ref="container">
    <img v-for="(i, index) in pics" class="layers" :key="index" :src="i.layerSrc" :alt="index + ''" :style="{
      zIndex: 50 - index
    }" />
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref, computed, ComputedRef } from "vue";

interface iMultiLayer {
  pics: Array<{ layerSrc: string, lock?: boolean }>;
  width?: number | string;
  height?: number | string;
}

withDefaults(defineProps<iMultiLayer>(), {
  width: "100%",
  height: "100%"
});

let viewWidth: number = 0;
let containerPosition: number = 0;
let left = ref<number>(50);

const abLeft = computed(() => {
  return left.value + '%'
})

const transLeft = computed(() => {
  return -left.value + '%'
})

const container = ref<HTMLInputElement | null>(null);
const mouseMove = (e: MouseEvent) => {
  const diffX = e.clientX - containerPosition - viewWidth / 2;
  console.log(left.value);
  left.value = 50 + 100 * diffX / viewWidth
};

onMounted(() => {
  containerPosition = container.value?.offsetLeft ?? 0;
  viewWidth = container.value?.offsetWidth ?? 0;
});
</script>

<style scoped lang="less">
#multi-layer-container {
  display: flex;
  justify-content: center;
  position: relative;
  box-sizing: border-box;
  width: v-bind(width);
  height: v-bind(height);
  border: 3px solid black;
  overflow: hidden;

  .layers {
    position: absolute;
    height: 100%;
    left: v-bind(abLeft);
    transform: translateX(v-bind(transLeft));
    transition: all .3s
  }
}
</style>