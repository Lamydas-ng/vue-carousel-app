<template>
  <div class="carousel">
    <div class="carousel-inner" :style="dimention">
     
      <carousel-item
        v-for="(slide, index) in slides"
        :slide="slide"
        :key="`slide-${index}`"
        :current-slide="currentSlide"
        :index="index"
        :direction="direction"
    
      ></carousel-item>
      <carousel-controls
        v-if="controls"
        @prev="prev"
        @next="next"
      ></carousel-controls>
    </div>
  </div>
</template>

<script>
import CarouselItem from "./CarouselItem.vue";
import CarouselControls from "./CarouselControls.vue";
import CarouselIndicators from "./CarouselIndicators.vue";

export default {
  props: {
    slides: {
      type: Array,
      required: true,
    },
    controls: {
      type: Boolean,
      default: false,
    },
    indicators: {
      type: Boolean,
      default: false,
    },
    interval: {
      type: Number,
      default: 5000,
    },
    width: {
      type: Number,
      default: 900,
    },
    height: {
      type: Number,
      default: 400,
    },
  },
  computed: {
    dimention() {
      return {
        width: this.width + "px",
        height: this.height + "px",
      };
    },
  },
  components: { CarouselItem, CarouselControls, CarouselIndicators },
  data: () => ({
    currentSlide: 0,
    slideInterval: null,
    direction: "right",
  }),

  mounted(){
        
    this.startSliderTimer();

    },

    beforeUnmount(){
     this.stopSliderTimer();
    },

    methods: {

      startSliderTimer(){
        this.stopSliderTimer();
        this.slideInterval = setInterval( ()=>{
           this._next();
        },3000);

      },

      stopSliderTimer(){
        clearInterval(this.slideInterval );
      },

        setCurrentSlide(index){
            this.currentSlide = index; 

        },
        next(){
           this._next();
           this.startSliderTimer();
        },
        prev(){
            const index = this.currentSlide > 0 ? this.currentSlide -1 : this.slides.length -1 ; 
           this.setCurrentSlide(index);
           this.direction = "right";
           this.startSliderTimer();
        },
        _next(){
          const index = this.currentSlide < this.slides.length -1 ? this.currentSlide + 1 : 0; 
           this.setCurrentSlide(index);
           this.direction = "left";
        },


    }

};
</script>

<style scoped>
.carousel {
  display: flex;
  justify-content: center;
  align-content: center;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
}
</style>
