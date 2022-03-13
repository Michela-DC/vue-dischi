<template>
  <div class="select-wrapper">
        <select name="select" id="select" v-model="selected" @change="$emit('select', selected)">
        <!-- invece che passare a @change la funzione selectGenre() dove ho dentro $emit posso passare direttamente $emit nel tag ed ho lo stesso risultato (non vedrò solo il console.log perché è della funzione) -->
            <option value="">Choose a genre or an artist</option>

            <optgroup label="Genres">
                <option v-for="genre in getGenre" :key="genre" >{{genre}}</option>
            </optgroup>

            <optgroup label="Artists">
                <option v-for="artist in getAuthor" :key="artist" >{{artist}}</option>
            </optgroup>

        </select>
    </div>
</template>

<script>
export default {
    name: 'SelectBar',
    data() {
        return {
            selected: '',
        }
    },
    props: {
        albumsOptions: Array,
    },   
    computed: {
        getGenre: function () {

            const genresArray = [];

            for(let i = 0; i < this.albumsOptions.length; i++){
                if(!genresArray.includes(this.albumsOptions[i].genre)) {
                    genresArray.push(this.albumsOptions[i].genre);
                }
            }
            console.log(genresArray)
            return genresArray
        },

        getAuthor: function () {

            const authorsArray = [];

            // recupero gli autori ciclando dentro this.albums con un forEach e li pusho dentro all'array authorsArray
            this.albumsOptions.forEach(element => authorsArray.push(element.author));
            console.log(authorsArray);
            return authorsArray;
        }
    }

    // methods: {
    //     selectGenre: function() {
    //         console.log(this.selected);
    //         this.$emit('select', this.selected); 
    //     }
    // }

}
</script>

<style scoped lang="scss">

.select-wrapper {
// margin: 0 auto;
// padding-right: 44px; 
position: absolute;
height: 65px;
top: 0;
display: flex;
align-items: center;
gap: 30px;

    #select{
        width: 250px;
        height: 30px;
        border: none;
        border-radius: 5px;
        padding: 0 15px;
    }
}

</style>