<template>
  <div class="slider">
    <slider-counter
      :numberOfSlides="images.length"
      :currentSlideIndex="imageIndex"
    />
    <slider-slide-item :image="currentSlide" @nextSlide="nextSlide" />
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, ref, computed } from "vue";
import SliderSlideItem from "./SliderSlideItem.vue";

import SliderSlide from "../types/SliderSlide";
import SliderCounter from "./SliderCounter.vue";

export default defineComponent({
  components: { SliderSlideItem, SliderCounter },
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

<style scoped>
.slider {
  position: relative;
  width: 100%;
  height: 600px;
  padding: 110px 0px 0px 190px;
  box-sizing: border-box;
}

@media screen and (max-width: 870px) {
  .slider {
    padding: 110px 100px;
  }
}

@media screen and (max-width: 750px) {
  .slider {
    padding: 90px 100px;
  }
}

@media screen and (max-width: 650px) {
  .slider {
    padding: 80px 20px;
  }
}
</style>
