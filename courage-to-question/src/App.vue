<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/ctq-hero.jpg"> -->
    <Main headline="Courage to Question"/>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Main,
  }
}
</script>

<style>
body,
html {
  width: 100%;
  height: 100%;
}

body {
  color: #2c3e50;
  position: relative;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
  font-size: 18px;
  font-weight: 400;
  letter-spacing: .1px;
  line-height: 28px;
  font-family: 'Open Sans', sans-serif, Helvetica, Arial, sans-serif;
  text-align: left;
}

h1 {
  font-size: 28px;
  font-weight: 300;
  letter-spacing: initial;
  line-height: 36px;
  text-align: center;
  margin: 0 0 54px 0;
}

p {
  font-size: 18px;
  line-height: 1.75;
  letter-spacing: 0;
  margin: 0 0 24px 0;
}

img,
video {
  display: block;
  width: 100%;
  max-width: 100%;
  height: auto;
}

footer {
  padding-top: 100px;
}

@media (min-width: 1024px) {
  h1 {
    font-size: 48px;
    font-weight: 300;
    letter-spacing: -.5px;
    line-height: 56px;
  }

  p {
    font-size: 22px;
    margin: 0 0 54px 0;
  }
}

</style>
