<template>
  <div>
    <pre>{{ image }}</pre>
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
    },
  },
  setup(props, { emit }) {
    setInterval(() => {
      emit("nextSlide");
    }, 5000);
  },
});
</script>
