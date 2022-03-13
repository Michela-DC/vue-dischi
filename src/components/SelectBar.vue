<template>
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
</template>

<script>
export default {
    name: 'SelectBar',
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


.select-wrapper {
// margin: 0 auto;
// padding-right: 44px; 
position: absolute;
height: 65px;
top: 0;
display: flex;
align-items: center;

    #select-genre{
        width: 250px;
        height: 30px;
        border: none;
        border-radius: 5px;
        padding: 0 15px;
    }
}

    
</style>