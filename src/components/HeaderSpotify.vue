<template>
  <header>
      <div class="header-container">
            <figure class="logo-wrapper">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Spotify.png/600px-Spotify.png" alt="">
            </figure>

            <div class="select-wrapper">
                <select name="select-genres" id="select-genre" v-model="selected" @change="$emit('select', selected)">
                <!-- invece che passare a @change la funzione selectGenre() dove ho dentro $emit posso passare direttamente $emit nel tag ed ho lo stesso risultato (non vedrò solo il console.log perché è della funzione) -->
                        <option disabled value="">Choose a genre</option>
                        <option value="Jazz">Jazz</option>
                        <option value="Metal">Metal</option>
                        <option value="Rock">Rock</option>
                        <option value="Pop">Pop</option> 
                </select>
            </div>
      </div> 
  </header>
</template>

<script>

export default {
    name: 'HeaderSpotify',
    data() {
        return {
            selected: '',
        }
    },
    // methods: {
    //     selectGenre: function() {
    //         console.log(this.selected);
    //         this.$emit('select', this.selected); 
    //     }
    // }
}
</script>

<style scoped lang="scss">

header{
    // background-color: #2E3A46;
    background-color: rgba(white, 0.1);
    position: fixed;
    left: 0;
    right: 0;
    top: 0;
}

.header-container{
    height: 65px;
    display: flex;
    align-items: center;
    padding: 0 23px;

    .logo-wrapper{
        width: fit-content;

        img{
            height: 44px;
            display: block;
        }
    }

    .select-wrapper {
    margin: 0 auto;
    padding-right: 44px; 

        #select-genre{
            width: 250px;
            height: 30px;
            border: none;
            border-radius: 5px;
            padding: 0 15px;
        }
    }
}
    
</style>