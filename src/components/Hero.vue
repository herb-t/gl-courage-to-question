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

  .ctq__hero-image,
  .ctq__hero-layer {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .ctq__hero-layer--phone {
    z-index: 1;
  }

  .ctq__hero-layer--back {
    z-index: 5;
  }

  .ctq__hero-layer--front {
    z-index: 10;
  }

  .ctq__hero-layer--clouds {
    z-index: 15;
  }

  .ctq__hero-layer--headline {
    z-index: 20;
  }

  @media (min-width: 800px) {
    .ctq__hero {
      padding-bottom: 77%;
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

        <div class="ctq__hero-layer ctq__hero-layer--phone">
          <picture class="ctq__hero-picture">
            <source media="(max-width: 799px)" srcset="../assets/mobile-phone.png">
            <source media="(min-width: 800px)" srcset="../assets/desktop-phone.png">
            <img src="../assets/desktop-phone.png" class="ctq__hero-layer-image" alt="" role="presentation">
          </picture>
        </div>

        <div class="ctq__hero-layer ctq__hero-layer--front">
          <picture class="ctq__hero-picture">
            <source media="(max-width: 799px)" srcset="../assets/mobile-front.png">
            <source media="(min-width: 800px)" srcset="../assets/desktop-front.png">
            <img src="../assets/desktop-front.png" class="ctq__hero-layer-image" alt="" role="presentation">
          </picture>
        </div>

        <div class="ctq__hero-layer ctq__hero-layer--back">
          <picture class="ctq__hero-picture">
            <source media="(max-width: 799px)" srcset="../assets/mobile-back.png">
            <source media="(min-width: 800px)" srcset="../assets/desktop-back.png">
            <img src="../assets/desktop-back.png" class="ctq__hero-layer-image" alt="" role="presentation">
          </picture>
        </div>

        <div class="ctq__hero-layer ctq__hero-layer--clouds">
          <picture class="ctq__hero-picture">
            <source media="(max-width: 799px)" srcset="../assets/mobile-clouds.png">
            <source media="(min-width: 800px)" srcset="../assets/desktop-clouds.png">
            <img src="../assets/desktop-clouds.png" class="ctq__hero-layer-image" alt="" role="presentation">
          </picture>
        </div>

        <div class="ctq__hero-layer ctq__hero-layer--headline">
          <picture class="ctq__hero-picture">
            <source media="(max-width: 799px)" srcset="../assets/mobile-headline.png">
            <source media="(min-width: 800px)" srcset="../assets/desktop-headline.png">
            <img src="../assets/desktop-headline.png" class="ctq__hero-layer-image" alt="" role="presentation">
          </picture>
        </div>

      </div>
    </div>
  </section>
</template>

<script>

import Bowser from "bowser";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'Hero',
  props: {
    title: String
  },
  data () {
    return {
      mobile: [
        '/images/mobile-phone.png', 
        '/images/mobile-back.png',
        '/images/mobile-front.png', 
        '/images/mobile-clouds.png',
        '/images/mobile-headline.png'
      ],
      desktop: [
        '/images/desktop-phone.png', 
        '/images/desktop-back.png',
        '/images/desktop-front.png', 
        '/images/desktop-clouds.png',
        '/images/desktop-headline.png'
      ]
    }
  },
  mounted: function() {
    const browser = Bowser.getParser(window.navigator.userAgent);
    const platform = browser.getPlatformType();
    const isMobile = platform === 'mobile' || platform === 'tablet';

    function imagesAreLoaded() {
      gsap.to(".ctq__hero", {
        autoAlpha: 1,
        ease: "Power4.easeOut",
        duration: .4
      });
      this.init();
    }

    this.loadImages(
        isMobile ? this.mobile : this.desktop,
        imagesAreLoaded.bind(this));

  },
  methods: {
    init: function() {
      var tl = gsap.timeline({
        defaults: { ease: "none", transformOrigin: "50% 50%" },
        scrollTrigger:{
          trigger:".ctq__hero",
          scrub: .6,
          pin: false,
          start:"top top",
          end: "bottom +=100px",
          markers: true
      }});

      tl.to('.ctq__hero-layer--phone', {
        y: 200,
        duration: 6,
      });
      tl.to('.ctq__hero-layer--back', {
        y: 150,
        duration: 6,
      }, '-=6');
      tl.to('.ctq__hero-layer--front', {
        y: 100,
        duration: 6,
      }, '-=6');
      tl.to('.ctq__hero-layer--clouds', {
        y: 50,
        duration: 6,
      }, '-=6');
      tl.to('.ctq__hero-layer--headline', {
        y: 75,
        duration: 6,
      }, '-=6');

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
