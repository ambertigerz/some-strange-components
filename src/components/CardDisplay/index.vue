<template>
  <div id="card-display">
    <div
      v-for="(i, index) in cards"
      :key="i.name"
      :class="[index, 'card']"
      :style="{
        height:
          100 -
            (200 * Math.abs(firstImgIndex + (displayNum - 1) / 2 - index)) /
              (displayNum + 1) >
          0
            ? 100 -
              (200 * Math.abs(firstImgIndex + (displayNum - 1) / 2 - index)) /
                (displayNum + 1) +
              '%'
            : 0,
        // transform: `translate(${
        //   20 * firstImgIndex + 10 * (displayNum - 1) - 20 * index
        // }%)`,
        zIndex:
          cards.length +
          100 -
          Math.abs(firstImgIndex + (displayNum - 1) / 2 - index),
        // display:
        //   100 -
        //     (200 * Math.abs(firstImgIndex + (displayNum - 1) / 2 - index)) /
        //       (displayNum + 1) >
        //   0
        //     ? `flex`
        //     : `none`,
        aspectRatio: 1 / aspectRatio,
        backgroundImage: `url(${i.src})`,
        opacity:
          100 -
            (200 * Math.abs(firstImgIndex + (displayNum - 1) / 2 - index)) /
              (displayNum + 1) >
          0
            ? 1
            : 0,
      }"
      @click="switchCard(index)"
    >
      <div
        class="card-model"
        :style="{
          fontSize:
            100 -
            (200 * Math.abs(firstImgIndex + (displayNum - 1) / 2 - index)) /
              (displayNum + 1) +
            '%',
        }"
      >
        {{ i.name }}
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref, computed, ComputedRef } from "vue";

interface iCardDisplay {
  cards: Array<{ src: string; name: string | number; desc?: string | number }>;
  displayNum?: number;
  aspectRatio?: number;
  width?: number | string;
  height?: number | string;
}

const props = withDefaults(defineProps<iCardDisplay>(), {
  width: "100%",
  height: "100%",
  displayNum: 5,
  aspectRatio: 2,
});

const firstImgIndex = ref<number>(0);

const switchCard = (index: number) => {
  //   firstImgIndex.value = index - (props.displayNum - 1) / 2;
  const changeIndex = (type: "+" | "-") => {
    setTimeout(() => {
      type === "+" ? firstImgIndex.value++ : firstImgIndex.value--;
      if (index === firstImgIndex.value + (props.displayNum - 1) / 2) {
        return;
      } else {
        changeIndex(type);
      }
    }, 150);
  };
  if (index > firstImgIndex.value + (props.displayNum - 1) / 2) {
    changeIndex("+");
  } else if (index < firstImgIndex.value + (props.displayNum - 1) / 2) {
    changeIndex("-");
  }
};
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
    box-sizing: border-box;
    padding: 0;
    transition: all 0.3s;
    background-size: 100% 100%;

    &:hover {
      filter: drop-shadow(0 0 20px rgba(255, 250, 190, 0.7));
      & .card-model {
        opacity: 1;
      }
    }

    &-model {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.7);
      color: white;
      font-weight: bold;
      transition: all 0.3s;
      opacity: 0;
    }
  }
}
</style>
