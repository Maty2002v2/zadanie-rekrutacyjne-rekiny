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

    <div class="content">
      <h1 class="content__h1">{{ image.header }}</h1>
      <h2 class="content__h2">{{ image.subheader }}</h2>
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
import { defineComponent, PropType, onBeforeUnmount } from "vue";

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
    const interval = setInterval(() => {
      emit("nextSlide"); //TODO:w destroy wyczyscic
    }, 5000);

    onBeforeUnmount(() => clearInterval(interval));
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
  opacity: 1;
  z-index: -1000;
}

.slide-item__darkening {
  background: #000000;
  opacity: 0.5;
  z-index: -999;
}

.content__h1 {
  margin-bottom: 5px;
  font-size: 50px;
}

.content__h2 {
  margin: 0 0 15px 30px;
  font-weight: 400;
}

.slide-item__button {
  width: 170px;
  height: 40px;
  border: none;
  border-radius: 5px;
  margin: 30px 30px 0 0;
  box-sizing: border-box;

  color: #ffffff;
  font-size: 11px;

  background: #40e17e;
}

.slide-item__button--outline {
  border: 2px solid #40e17e;
  background: transparent;
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
