<template>
    <div id="card-display">
        <div v-for="(i,index) in cards" :key="i.name" :class="[index,'card']"
            :style="{height:(200*firstImgIndex-200*index+200)/(displayNum+1)+'%'}">
            <img :src="i.src">
        </div>
    </div>
</template>

<script setup lang="ts">
import { onMounted, ref, computed, ComputedRef } from "vue";

interface iCardDisplay {
    cards: Array<{ src: string, name: string | number, desc?: string | number }>;
    displayNum?: number;
    aspectRatio?: number;
    width?: number | string;
    height?: number | string;
}

const firstImgIndex = ref<number>(0);

withDefaults(defineProps<iCardDisplay>(), {
    width: "100%",
    height: "100%",
    displayNum: 5,
    aspectRatio: 2,
})
</script>

<style lang="less" scoped>
#card-display {
    display: flex;
    justify-content: center;
    align-items: center;
    width: v-bind(width);
    height: v-bind(height);
    padding: 10px;
    box-sizing: border-box;

    .card {
        display: flex;
        justify-content: center;
        align-items: center;
        border: 2px solid black;
        box-sizing: border-box;
    }
}
</style>