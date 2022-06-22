<template>
  <div class="slider-timer"><span class="slider-timer--span"></span></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SliderTimer",
  props: {
    time: {
      type: Number,
      required: true,
    },
  },
});
</script>

<style>
.slider-timer {
  width: 350px;
  height: 1px;
  background: #ffffff;
}

.slider-timer--span {
  display: block;
  width: 100%;
  height: 100%;
  background: #40e17e;
  animation: countdown 5s ease-in-out alternate;
}

@keyframes countdown {
  0% {
    width: 100%;
  }
  9% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}
</style>
