<template>
  <div class="container">
    <nav class="container__navbar">MENU</nav>
    <the-slider class="container__slider" :images="FETCH_IMAGES" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TheSlider from "./components/TheSlider.vue";

import SliderSlide from "./types/SliderSlide";

import "@/styles/GlobalStyles.css";

export default defineComponent({
  name: "App",
  components: {
    TheSlider,
  },
  setup() {
    const FETCH_IMAGES: SliderSlide[] = [
      //lub bardziej content niż images
      {
        nameImage: "1.jpg",
        header: "Quisque vulputate mi consectetur",
        subheader: "Quisque vulputate mi consectetur",
        content:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed posuere quis mi a fermentum. Nulla vel fringilla quam. Quisque a nulla euismod, finibus est eu, molestie lectus. Nam rhoncus nec nibh sit amet rhoncus. Donec mauris dolor, suscipit a felis auctor, dignissim imperdiet mi. Nulla facilisi. Praesent lobortis in purus in bibendum. Pellentesque eleifend, dui sit amet scelerisque hendrerit, mauris diam fermentum massa, et posuere nisl orci sed mi. In leo libero, sollicitudin eu felis in, egestas ultrices dui. Integer sed libero egestas, faucibus lectus ac, consectetur enim.",
      },
      {
        nameImage: "2.jpg",
        header: "Pellentesque eleifend, dui sit amet",
        subheader: "Mauris diam fermentum massa.",
        content:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed posuere quis mi a fermentum. Nulla vel fringilla quam. Quisque a nulla euismod, finibus est eu, molestie lectus. Nam rhoncus nec nibh sit amet rhoncus. Donec mauris dolor, suscipit a felis auctor, dignissim imperdiet mi. Nulla facilisi. Praesent lobortis in purus in bibendum. Pellentesque eleifend, dui sit amet scelerisque hendrerit, mauris diam fermentum massa, et posuere nisl orci sed mi. In leo libero, sollicitudin eu felis in, egestas ultrices dui. Integer sed libero egestas, faucibus lectus ac, consectetur enim.",
      },
      {
        nameImage: "3.jpg",
        header: "Nam rhoncus nec nibh sit amet",
        subheader: "Donec mauris dolor, suscipit a felis auctor.",
        content:
          "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed posuere quis mi a fermentum. Nulla vel fringilla quam. Quisque a nulla euismod, finibus est eu, molestie lectus. Nam rhoncus nec nibh sit amet rhoncus. Donec mauris dolor, suscipit a felis auctor, dignissim imperdiet mi. Nulla facilisi. Praesent lobortis in purus in bibendum. Pellentesque eleifend, dui sit amet scelerisque hendrerit, mauris diam fermentum massa, et posuere nisl orci sed mi. In leo libero, sollicitudin eu felis in, egestas ultrices dui. Integer sed libero egestas, faucibus lectus ac, consectetur enim.",
      },
    ];

    return { FETCH_IMAGES };
  },
});
</script>

<style>
.container {
  box-sizing: border-box;
  width: 100%;
}

.container__navbar {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 26px;
  box-sizing: border-box;

  color: #d8d8d8;
  font-family: Work Sans;
  font-size: 20px;
  font-weight: 700;
  letter-spacing: 1px;

  background: #eaeaea;
}

.container__slider {
  display: flex;
  flex-direction: column;
}
</style>
