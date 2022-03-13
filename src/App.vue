<template>
  <div id="app">
    <!-- con v-on ascolto l'evento che ho chiamato select nell'emit  e gli passo la funzione che riceve i dati dell'evento select e li salva dentro a selctedOptions-->
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
    HeaderSpotify,
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
