<template>
  <div class="slider-counter">
    <span
      v-for="(number, index) in numberOfSlides"
      :key="number"
      :ref="setItemRef"
      :class="{ 'slider-counter__span--active': index === 0 }"
      class="slider-counter__span"
    ></span>
  </div>
</template>

<script lang="ts">
import { defineComponent, onBeforeUpdate, onUpdated } from "vue";

export default defineComponent({
  name: "SliderCounter",
  props: {
    numberOfSlides: {
      type: Number,
      required: true,
    },
    currentSlideIndex: {
      type: Number,
      required: true,
    },
  },
  setup(props) {
    let itemRefs: HTMLElement[] = [];

    const setItemRef = (el: HTMLElement) => {
      if (el) {
        itemRefs.push(el);
      }
    };

    onBeforeUpdate(() => {
      itemRefs = [];
    });

    onUpdated(() => {
      itemRefs[
        props.currentSlideIndex - 1 >= 0
          ? props.currentSlideIndex - 1
          : props.numberOfSlides - 1
      ].classList.remove("slider-counter__span--active");

      itemRefs[props.currentSlideIndex].classList.add(
        "slider-counter__span--active"
      );
    });

    return { setItemRef };
  },
});
</script>

<style>
.slider-counter__span {
  display: inline-block;
  width: 9px;
  height: 9px;
  border-radius: 50%;
  margin-right: 10px;

  background: #ffffff;

  opacity: 0.1;
  transition: all 0.5s linear;
}

.slider-counter__span--active {
  opacity: 1;
  transform: scale(1.2);
}
</style>
