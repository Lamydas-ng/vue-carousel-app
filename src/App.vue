<template>
  <Div class="justifyme"> 
    <Carousel :slides="slides"></Carousel>
  </Div>

</template>

<script>
import  Carousel from "./components/carousel/Carousel.vue";
export default{
 components:  {Carousel} ,
  data: () => ({
    slides: [
      "src/assets/img/slide-1.jfif",
      "src/assets/img/slide-2.jfif",
      "src/assets/img/slide-3.jfif",
      "src/assets/img/slide-4.jfif",
      "src/assets/img/slide-5.jfif",
     
    ],
  }),
}
</script>


<style scoped>
   .justifyme {
        justify-self: center;
        display: flex;
        flex-direction: row;

        
    }
</style>


