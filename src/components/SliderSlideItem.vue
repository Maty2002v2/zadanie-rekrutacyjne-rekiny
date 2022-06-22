<template>
  <div class="slide-item">
    <Transition name="fade">
      <img
        class="slide-item__bg-img"
        :src="require('@/assets/' + image.nameImage)"
        :key="image.nameImage"
        alt="slider backgraund"
      />
    </Transition>
    <div class="slide-item__darkening"></div>

    <div class="slide-item__content">
      <h1>{{ image.header }}</h1>
      <h2>{{ image.subheader }}</h2>
      <p>{{ image.content }}</p>
    </div>
    <button>DOLOR SIT AMENT</button>
    <button>LOREM IPSUM</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import SliderSlide from "../types/SliderSlide";

export default defineComponent({
  name: "SliderSlideItem",
  props: {
    image: {
      type: Object as PropType<SliderSlide>,
      required: true,
    },
  },
  setup(props, { emit }) {
    setInterval(() => {
      emit("nextSlide");
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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
