<style scoped>

  .ctq__section--hero {
    background-image: linear-gradient(#ffbabf, #fbdfc9);
    overflow: hidden;
  }

  .ctq__hero {
    height: 0;
    opacity: 0;
    padding-bottom: 178%;
    position: relative;
    transition: opacity .4s ease-out;
  }

  .ctq__hero-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .ctq-images-loaded {
    opacity: 1;
  }

  @media (min-width: 800px) {
    .ctq__hero {
      padding-bottom: 77%;
    }
  }

  @media (min-width: 1440px) {
    .ctq__row--sml {
      max-width: 1280px;
      padding: 0 72px;
    }
  }

  @media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) {
    .ctq__hero {
      max-height: 625px;
    } 
  }

  @media only screen and (min-device-width: 1024px) and (max-device-width: 1024px) and (orientation: portrait) and (-webkit-min-device-pixel-ratio: 2) {
    .ctq__hero {
      max-height: 790px;
    } 
  }

</style>

<template>
  <section class="ctq__section ctq__section--hero">
    <div class="ctq__section-content">
      <div class="ctq__hero">        
        <div class="ctq__hero-image">
          <picture class="ctq__hero-picture">
            <source media="(max-width: 799px)" srcset="../assets/ctq-hero-mobile.png">
            <source media="(min-width: 800px)" srcset="../assets/ctq-hero-desktop.png">
            <img src="../assets/ctq-hero-desktop.png" class="ctq__hero-background" alt="">
          </picture>
        </div>
      </div>
    </div>
  </section>
</template>

<script>

import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'Hero',
  props: {
    title: String
  },
  mounted: function() {

    function imagesAreLoaded() {
      document.querySelector('.ctq__hero').classList.add('ctq-images-loaded');
      // this.init();
      const tl = gsap.timeline({scrollTrigger:{
          trigger: ".ctq__hero",
          scrub: true,
          pin: false,
          start:"top top",
          end: "+=100%",
          markers: false
      }});

      tl.to('.ctq__hero-image', {
        y: 150,
        duration: 6
      })
    }

    this.loadImages([
      'https://storage.googleapis.com/hook-2017.appspot.com/projects/courage-to-question/ctq-hero-desktop.png', 
      'https://storage.googleapis.com/hook-2017.appspot.com/projects/courage-to-question/ctq-hero-mobile.png'
    ], imagesAreLoaded);

  },
  methods: {
    init: function() {
      const tl = gsap.timeline({scrollTrigger:{
          trigger:".ctq__hero-image",
          scrub: true,
          pin: false,
          start:"top top",
          end: "+=100%",
          markers: true
      }});

      tl.to('.ctq__hero-picture', {
        y: -700,
        duration: 6
      })

      return tl;
    },
    loadImages: function(a, d, z) {
      var isFunction = isFunction || function(functionToCheck) {
        var getType = {};
        return functionToCheck && getType.toString.call(functionToCheck) == '[object Function]';
      }

      a instanceof Array || (a = [a]);
      for (var e = a.length, f = 0, g = e; g--;) {
        var b = document.createElement("img");
        b.onload = function() {
          f++; 
          f >= e && isFunction(d) && d(z)
        };
        b.src = a[g]; 
      }
    }
  },
}

</script>
