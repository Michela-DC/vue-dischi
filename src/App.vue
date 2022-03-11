<template>
  <div id="app">
    <HeaderSpotify/>
    <MainContent/>
  </div>
</template>

<script>

import HeaderSpotify from './components/HeaderSpotify.vue'
import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    MainContent,
    HeaderSpotify,
  }
}
</script>

<style lang="scss">

// @import '.assets/scss/common.scss';

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  // height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #1E2D3B;
}
</style>
