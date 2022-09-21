<template>
  <div> <carousel
    :slides="slides"
    controls
    indicators
    :interval="3000"
    :width="1000"
    :height="450"
  ></carousel></div>
 
</template>

<script>
import Carousel from "./components/carousel/Carousel.vue";

export default {
  components: { Carousel },
  data: () => ({
    slides: [
    "src/assets/img/food-1.jpg",
    "src/assets/img/food-2.jpg",
    "src/assets/img/food-3.jpg",
    "src/assets/img/food-4.jpg",
     "src/assets/img/food-5.jpg",
    "src/assets/img/slide-3.jpg",
    "src/assets/img/slide-5.jpg",
    ],
  }),
};
</script>

<style></style>
