<template>
  <div><slider-slide-item /></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SliderSlideItem from "./SliderSlideItem.vue";

export default defineComponent({
  components: { SliderSlideItem },
  name: "TheSlider",
  props: {
    images: Array,
  },
});
</script>
