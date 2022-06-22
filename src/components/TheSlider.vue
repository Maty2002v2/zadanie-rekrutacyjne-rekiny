<template>
  <div class="slider">
    <slider-slide-item :image="currentSlide" @nextSlide="nextSlide" />
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, ref, computed } from "vue";
import SliderSlideItem from "./SliderSlideItem.vue";

import SliderSlide from "../types/SliderSlide";

export default defineComponent({
  components: { SliderSlideItem },
  name: "TheSlider",
  props: {
    images: {
      type: Array as PropType<SliderSlide[]>,
      required: true,
    },
  },
  setup(props) {
    let imageIndex = ref(0);

    function nextSlide() {
      imageIndex.value + 1 < props.images.length
        ? imageIndex.value++
        : (imageIndex.value = 0);
    }

    const currentSlide = computed(() => props.images[imageIndex.value]);

    return { imageIndex, currentSlide, nextSlide };
  },
});
</script>

<style>
.slider {
  position: relative;
  height: 600px;
  padding-top: 120px;
  box-sizing: border-box;
  overflow: hidden;
}
</style>
