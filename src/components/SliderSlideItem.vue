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
      <p class="content__p">{{ image.content }}</p>
    </div>

    <div class="button-container">
      <button class="button-container__button">LOREM IPSUM</button>
      <button
        class="button-container__button button-container__button--outline"
      >
        DOLOR SIT AMENT
      </button>
    </div>
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
  width: 100%;
  color: #ffffff;
  font-weight: 900;
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
  object-fit: cover;
  opacity: 1;
  z-index: -1000;
}

.slide-item__darkening {
  background: #000000;
  opacity: 0.5;
  z-index: -999;
}

.content__h1 {
  margin: 5px 0px;
  font-family: Work Sans;
  font-size: 50px;
}

.content__h2 {
  margin: 0 0 15px 30px;
  font-family: Work Sans;
  font-size: 30px;
  font-weight: 300;
  letter-spacing: 3px;
}

.content__p {
  display: -webkit-box;
  -webkit-line-clamp: 4;
  -webkit-box-orient: vertical;
  max-width: 650px;
  overflow: hidden;

  font-size: 13px;
  font-weight: 200;
  line-height: 25px;
}

.button-container {
  display: flex;
}

.button-container__button {
  width: 170px;
  height: 40px;
  border: none;
  border-radius: 5px;
  margin: 30px 30px 0px 0px;
  box-sizing: border-box;

  color: #ffffff;
  font-size: 11px;

  background: #40e17e;
}

.button-container__button--outline {
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

@media screen and (max-width: 750px) {
  .slide-item {
    margin: 20px 30px 0px 0px;
  }

  .content__h1 {
    font-size: 40px;
  }

  .content__h2 {
    font-size: 22px;
  }
}

@media screen and (max-width: 650px) {
  .slide-item {
    margin: 20px 30px 0px 0px;
  }

  .content__h1 {
    font-size: 29px;
    font-weight: 700;
  }

  .content__h2 {
    font-size: 17px;
    font-weight: 200;
  }

  .content__p {
    font-size: 15px;
    font-weight: 500;
    letter-spacing: 1px;
  }
}

@media screen and (max-width: 600px) {
  .button-container {
    flex-direction: column-reverse;
  }

  .button-container__button {
    width: 190px;
    height: 55px;
    margin: 20px 30px 0px 0px;
    font-size: 14px;
    letter-spacing: 1px;
  }

  .button-container__button--outline {
    width: 220px;
    border: 2px solid #40e17e;
    background: transparent;
  }
}
</style>
