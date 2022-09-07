<script setup lang="ts">
import { ref } from "vue";
import CardDisplay from "./components/CardDisplay/index.vue";
const list = ref([
  {
    name: "The Fool",
    src: "https://img.zcool.cn/community/01661a5f4f0afa11013f1a640f4a0b.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
  {
    name: "Wheel Of Fortune",
    src: "https://img.zcool.cn/community/01a5165f4f0afa11013e31871df737.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
  {
    name: "The High Priestess",
    src: "https://img.zcool.cn/community/01fc3f5f4f0afa11013e3187935ca7.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
  {
    name: "Death",
    src: "https://img.zcool.cn/community/019a575f4f0afa11013f1a64488c3c.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
  {
    name: "Wand",
    src: "https://img.zcool.cn/community/018b7c5f4f0afa11013e3187d1a54f.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
  {
    name: "Wand2",
    src: "https://img.zcool.cn/community/01c9775f4f0afa11013f1a644fc288.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
  {
    name: "Pentacle",
    src: "https://img.zcool.cn/community/01fbd95f4f0afa11013e318702a7ef.jpg?x-oss-process=image/auto-orient,1/resize,m_lfit,w_1280,limit_1/sharpen,100/format,webp/quality,q_100",
  },
]);
</script>

<template>
  <div id="app">
    <div style="width: 500px; height: 400px">
      <CardDisplay :cards="list" :display-num="9" />
    </div>
  </div>
</template>

<style lang="less" scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
