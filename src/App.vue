<template>
  <the-slider />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TheSlider from "./components/TheSlider.vue";

export default defineComponent({
  name: "App",
  components: {
    TheSlider,
  },
});
</script>
