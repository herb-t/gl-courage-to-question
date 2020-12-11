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
  font-size: 24px;
  font-weight: 400;
  letter-spacing: initial;
  line-height: 32px;
  text-align: center;
  margin: 0 0 54px 0;
}

p {
  font-size: 18px;
  line-height: 1.75;
  letter-spacing: 0;
  margin: 0 0 36px 0;
}

* > p:last-child {
  margin-bottom: 0;
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

@media (min-width: 600px) {
  h1 {
    font-size: 32px;
    font-weight: 400;
    letter-spacing: -.25px;
    line-height: 40px;
  }
}

@media (min-width: 1024px) {
  h1 {
    font-size: 36px;
    font-weight: 400;
    letter-spacing: -.25px;
    line-height: 44px;
  }

  p {
    font-size: 22px;
    margin: 0 0 54px 0;
  }
}

</style>

<template>
  <div id="app">
    <Main headline="Courage to Question"/>
  </div>
</template>

<script>
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Main,
  }
}
</script>
