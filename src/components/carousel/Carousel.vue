<template>
   
   <div class="carousel">
        <div class="carousel-inner">
            
            <CarouselItem v-for="(slide,index) in slides" 
            :slide="slide" 
            :key="`slide-${index}`" 
            :current-slide="currentSlide"
            :index="index"
            ></CarouselItem>
        </div>
   </div>
</template>
<script>    
import  CarouselItem from "./CarouselItem.vue";
export default{

    components:{
        CarouselItem
    },
    props:["slides"],
    data:
        ()=>({
           currentSlide: 0 ,
           slideInterval: null
        }),
    mounted(){
        this.slideInterval = setInterval( ()=>{
           const index = this.currentSlide > this.slides.length -1 ? 0 : this.currentSlide + 1
           this.setCurrentSlide(index);
        },3000);

       
    

    },

    beforeUnmount(){
        clearInterval(this.slideInterval )

    },

    methods: {
        setCurrentSlide(index){
            this.currentSlide = index; 

        }


    }



}

</script>
<style scoped>
    .carousel {
        justify-self: center;
        display: flex;
        flex-direction: row;

        
    }
    .carousel .carousel-inner {
      position: relative;
      overflow: hidden;
    }
    
    </style>
    