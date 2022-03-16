<template>
  <div id="app">
    <MainContent/>
  </div>
</template>

<script>

import MainContent from './components/MainContent.vue'

export default {
  name: 'App',
  components: {
    MainContent
  },
}

</script>

<style lang="scss">

@import './assets/scss/common.scss';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #1E2D3B;
  font-family: 'Roboto', sans-serif;;
}
</style>
