<template>
  <div class="slide-item">
    <Transition name="fade">
      <img
        class="slide-item__bg-img"
        :src="require('@/assets/' + image.nameImage)"
        :key="image"
        alt="slider backgraund"
      />
    </Transition>
    <div class="slide-item__darkening"></div>

    <div class="slide-item__content">
      <h1>{{ image.header }}</h1>
      <h2>{{ image.subheader }}</h2>
      <slider-timer :time="5" :key="image" />
      <p>{{ image.content }}</p>
    </div>

    <button class="slide-item__button">LOREM IPSUM</button>
    <button class="slide-item__button slide-item__button--outline">
      DOLOR SIT AMENT
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";

import SliderSlide from "../types/SliderSlide";
import SliderTimer from "./SliderTimer.vue";

export default defineComponent({
  components: { SliderTimer },
  name: "SliderSlideItem",
  props: {
    image: {
      type: Object as PropType<SliderSlide>,
      required: true,
    },
  },
  setup(props, { emit }) {
    setInterval(() => {
      emit("nextSlide"); //TODO:w destroy wyczyscic
    }, 5000);
  },
});
</script>

<style scoped>
.slide-item {
  width: 1000px;
  color: #ffffff;
  font-weight: 900;
  margin: 0 auto;
}

.slide-item__bg-img,
.slide-item__darkening {
  position: absolute;
  top: 0;
  left: 0;

  width: 100%;
  height: 100%;
}

.slide-item__bg-img {
  z-index: -1000;
  opacity: 1;
}

.slide-item__darkening {
  background: #000000;
  opacity: 0.5;
  z-index: -999;
}

.slide-item__content {
}

.slide-item__button {
  border: none;
  border-radius: 5px;
  color: #ffffff;
  width: 170px;
  height: 40px;
  margin: 30px 30px 0 0;
  font-size: 11px;
  box-sizing: border-box;
  background: #40e17e;
}

.slide-item__button--outline {
  background: transparent;
  border: 2px solid #40e17e;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 1.1s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
