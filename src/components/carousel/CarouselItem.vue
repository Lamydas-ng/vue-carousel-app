<template>
   
   <transition name="slide-out">
     <div class="carousel-item" v-show="currentSlide===index">
        <img  :src="slide" width="900" height="400">
      </div>
   </transition>
</template>

<script>
    
export default  {

    props:["slide","index","currentSlide"],
    data: ()=>({
      cssItem: "carousel-item"
    })

}

</script>

<style scoped>
  .carousel-item {
 margin: 200px;
  }
  .slide-out-enter-active,
.slide-out-leave-active,
.slide-in-enter-active,
.slide-in-leave-active {
  transition: all 1s ease-in-out;
}
.slide-out-enter-from {
  transform: translateX(100%);
}
.slide-out-leave-to {
  transform: translateX(-100%);
}
.slide-in-enter-from {
  transform: translateX(-100%);
}
.slide-in-leave-to {
  transform: translateX(100%);
}
  
 
  </style>
  