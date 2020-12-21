<style>

  .ctq__section {
    box-sizing: border-box;
    margin-bottom: 120px;
  }

  .ctq__section--grey {
    background-color: #f7f7f7;
    padding: 100px 0;
  }

  .ctq__section--showcase {
    background-color: #fff;
    position: relative;
    z-index: 10;
  }

  .ctq__row {
    box-sizing: border-box;
    width: 100%;
    max-width: 1440px;
    margin: 0 auto;
    padding: 0 28px;
  }

  .ctq__row--sml {
    padding: 0 32px;
  }

  .ctq__video {
    box-shadow: 0 47px 80px -30px rgba(44, 43, 43, .75);
  }

  .ctq__video--website {
    box-shadow: 0 47px 80px -30px rgba(44,43,43,.23);
  }

  .ctq__video--stories {
    box-shadow: none;
  }

  .ctq__video:focus,
  .ctq__video:active {
    border: 0;
    outline: 0;
  }

  .border--top {
    transform: rotate(180deg);
  }

  .ctq-images-loaded {
    opacity: 1;
  }

  @media (min-width: 600px) {

    .ctq__row {
      padding: 0 40px;
    }

    .ctq__row--sml {
      padding: 0 calc(40px + 5%);
    }
  }

  @media (min-width: 1024px) {
    .ctq__section {
      margin-bottom: 200px;
    }

    .ctq__section--grey {
      padding: 200px 0;
    }

    .ctq__row {
      padding: 0 72px;
    }

    .ctq__row--sml {
      padding: 0 calc(72px + 10%);
    }
  }

  @media (min-width: 1440px) {
    .ctq__row--sml {
      max-width: 1280px;
      padding: 0 72px;
    }
  }

</style>

<template>
  <main class="ctq">

    <ctq_hero></ctq_hero>

    <section class="ctq__section ctq__section--showcase">
      <div class="ctq__section-content">
        <div class="ctq__row ctq__row--lrg">
          <div class="ctq__video">
            <video id="video_subhero" class="ctq__video-player ctq__video-player--ui" autoplay playsinline controls muted>
              <source src="../assets/videos/ctq-video-case-study_ff.mp4" type="video/mp4">
            </video>
          </div>
        </div>
      </div>
    </section>

    <section class="ctq__section">
      <div class="ctq__section-content">
        <div class="ctq__row ctq__row--sml">
          <div class="ctq__text">
            <p>
              One out of every three women experiences some form of gender-based violence worldwide. It’s an alarming statistic. That’s why, every year, Vital Voices Global Partnership puts on an event where extraordinary women working for change around the globe take center stage. The event draws thousands of attendees with guest speakers including activists, celebrities and politicians. Hundreds of portraits are created to celebrate these women and invest in their daring visions for positive, lasting change in their communities.
            </p>
            <p>
              To bring these portraits to life, we partnered with Google Lens and Vital Voices, creating a series of five “lenslets” which tell the moving stories of how these incredible women are fighting for change. Each lenslet is unlocked by scanning one of the portraits and reveals a woman’s story through her own words combined with animation. At the end of every Lens experience, viewers have the option to contribute to and learn more about each woman’s organization.
            </p>
          </div>
        </div>
      </div>
    </section>

    <section class="ctq__section">
      <div class="ctq__section-content">
        <div class="ctq__video">
          <video id="video_fullsize" class="ctq__video-player ctq__video-player--autoplay" autoplay loop playsinline muted>
            <source src="../assets/videos/ctq-video-showcase_ff.mp4" type="video/mp4">
          </video>
        </div>
      </div>
    </section>

    <section class="ctq__section ctq__section-spacing ctq__section--grey">
      <div class="ctq__section-content">
        <div class="ctq__section-title">
          <h1>STORIES WALL</h1>
        </div>
        <div class="ctq__row ctq__row--lrg">
          <div class="ctq__video ctq__video--stories">
            <video id="video_animations" class="ctq__video-player ctq__video-player--ui" autoplay playsinline controls muted>
              <source src="../assets/videos/ctq-video-animations_ff.mp4" type="video/mp4">
            </video>
          </div>
        </div>
      </div>
    </section>

    <section class="ctq__section">
      <div class="ctq__section-content">
        <div class="ctq__row ctq__row--lrg">
          <div class="ctq__section-title">
            <h1>WEBSITE</h1>
          </div>
          <div class="ctq__video ctq__video--website">
            <video id="video_website" class="ctq__video-player ctq__video-player--autoplay" autoplay loop playsinline muted>
              <source src="../assets/videos/ctq-video-site-mock.mp4_ff.mp4" type="video/mp4">
            </video>
          </div>
        </div>
      </div>
    </section>

    <footer></footer>

  </main>
</template>

<script>

import Hero from './Hero.vue';

export default {
  name: 'Main',
  components: {
    ctq_hero: Hero,
	},
  props: {
    headline: String
  },
  mounted: function() {
    const videos = document.querySelectorAll('.ctq__video-player--ui');

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        const video = entry.target;
        if (!entry.isIntersecting) {
          video.pause();
        } else {
          video.play();
        }
      });
    });

    videos.forEach(video => {
      observer.observe(video);
    });

  },
}

</script>
