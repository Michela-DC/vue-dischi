<template>
  <main>
    <div class="main-container">
        <AlbumsCards v-for="album in albums" :key="album.tile" :objectAlbum="album"/>
    </div>
  </main>
</template>

<script>

import axios from 'axios';
import AlbumsCards from './AlbumsCards.vue'

export default {
    name: 'MainContent',
    components: {
        AlbumsCards
    },

    data() {
        return {
            albums: [],
            // dentro questo array metterò gli elementi che ricevo dall'api
        }
    },
    // creo una funzione apposta per fare la chiamata e in questo modo in caso posso riutilizzarla
    methods: {
        fetchAlbums: function() {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then (res => {
                console.log(res.data);
                this.albums = (res.data.response);
                console.log(this.albums);
            })

            //recupero errori o risposte negative del server
            .catch( err => {
                console.warn(err.response)
            })
        }
    },
    // la chiamata al server la faccio nell'hook created perché è quando il componente è stato creato 
    created () {
        this.fetchAlbums();
    }
}
</script>

<style scoped lang="scss">

main{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.main-container{
    width: 70%;
    padding: 70px 0;
    display: flex;
    flex-wrap: wrap;
    gap: 3%;
}

</style>
    