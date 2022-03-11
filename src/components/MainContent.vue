<template>
  <main>
    <ul class="main-container">
        <AlbumsCards v-for="album in albums" :key="album.tile" :objectAlbum="album"/>
    </ul>
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
            // error = false,
        }
    },
    // creo una funzione apposta per fare la chiamata e in questo modo in caso posso riutilizzarla
    methods: {
        fetchAlbums: function() {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then (res => {
                // this.error = false; //se la chiamata va a buon fine allora imposto l'errore in falso
                console.log(res.data);
                this.albums = (res.data.response);
                console.log(this.albums);
            })

            //recupero errori o risposte negative del server
            .catch( err => {
                console.warn(err.response);
                // se la pagina va in errore resetto l'album e potrei anche mostrare un messaggio di errore
                this.albums = [];
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

@import '../assets/scss/common.scss';

main{
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 90px 20px 20px 20px;
}

.main-container{
    max-width: 1000px;
    display: flex;
    flex-wrap: wrap;
    gap: 20px 3%;
}

</style>
    