<template>
  <main>
    <!-- con v-on ascolto l'evento che ho chiamato select nell'emit  -->
    <SelectBar v-on:select="setOption" :albumsOptions="albums"/>

    <ul class="main-container">
        <AlbumsCards v-for="album in filteredGenreArtist" :key="album.title" :objectAlbum="album"/>
    </ul>
  </main>
</template>

<script>

import axios from 'axios';
import AlbumsCards from './AlbumsCards.vue'
import SelectBar from './SelectBar.vue'


export default {
    name: 'MainContent',
    components: {
        AlbumsCards,
        SelectBar,
    },

    data() {
        return {
            albums: [], // dentro questo array metterò gli elementi che ricevo dall'api
            selectedOption: '',
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
                console.log('array con dentro gli album',this.albums);
            })

            //recupero errori o risposte negative del server
            .catch( err => {
                console.warn(err.response);
                // se la pagina va in errore resetto l'album e potrei anche mostrare un messaggio di errore
                this.albums = [];
            })
        },

        // funzione che riceverà i dati dell'evento @select
        setOption: function(option){
            // dentro ad option viene salvato il dato selezionato con l'evento select
            console.log("ascoltato l'evento select e il dato è " + option);
            // salvo l'opzione scelta dentro alla selectedOption in modo che venga salvata dentro a qualcosa che poi possa essere stampato 
            this.selectedOption = option;
        },
    },

    computed: { 

        filteredGenreArtist: function () {
            // funzione in cui se la selectedOption è compresa tra i generi allora mi ritorna l'array con i generi filtrati
            // altrimenti mi ritorna l'array filtrato per artisti
            return this.albums.filter(album => { //album è l'elemento corrente

                if(album.genre.toLowerCase().includes(this.selectedOption.toLowerCase()) ){
                    console.log(album.genre.toLowerCase().includes(this.selectedOption.toLowerCase()))
                    return album.genre.toLowerCase().includes(this.selectedOption.toLowerCase());
                }else{
                    return album.author.toLowerCase().includes(this.selectedOption.toLowerCase());
                }
            })
            
        },
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
    // max-width: 1000px; se lascio max-width quando seleziono e mi mostra solo una card viene rimpicciolita in width
    width: 1000px;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px 3%;
}

</style>