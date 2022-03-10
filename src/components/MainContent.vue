<template>
  <main>
      <div class="mai-container">
          <AlbumsList/>
      </div>
  </main>
</template>

<script>
import AlbumsList from './AlbumsList.vue';

export default {
    name: 'MainContent',
    components: {
        AlbumsList 
    }
}
</script>

<style scoped lang="scss">
    
</style>