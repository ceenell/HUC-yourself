<template>
  <div id="visualization">

  </div>
</template>

<script>
import { ScrollToPlugin } from "gsap/ScrollToPlugin"; // to trigger scroll events
import { ScrollTrigger } from "gsap/ScrollTrigger"; // animated scroll events
export default {
    name: 'Visualization',
    components: {
    },
    computed: {
      checkIfSplashIsRendered() {
          return this.$store.state.splashRenderedOnInitialLoad;
      }
    },
    mounted(){
      const self = this;
      //Waits until the first DOM paint is complete
      //Allows us to only run the functionality when we know the DOM elements are loaded
      this.$gsap.registerPlugin(ScrollToPlugin, ScrollTrigger); // register gsap plugins for scrollTrigger
      this.$nextTick(function() {
        this.parallaxScroll();
      });
      //Wait for page to load then run this function
      window.addEventListener("load", function(){
        self.findCarouselContainers();
      });
    },
    updated(){
      this.lazyLoadImages();
    },
    methods:{
      
} 
}
</script>

<style lang="scss">
//Hides v-img title element
.title-v-img{
  display: none;
}
</style>
