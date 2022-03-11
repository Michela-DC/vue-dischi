<template>
    <div class="card-wrapper">

        <figure class="poster">
            <img :src="objectAlbum.poster" alt="">
        </figure>

        <div class="album-info">
            <h4 class="title">
                {{objectAlbum.title}}
            </h4>
            <div class="author">
                {{objectAlbum.author}}
            </div>
            <div class="genre">
                {{objectAlbum.genre}}
            </div>
            <div class="year">
                {{objectAlbum.year}}  
            </div>
        </div>
      
    </div>
</template>

<script>
export default {
    name: 'AlbumsCards',
    props: {
        objectAlbum: {
          type: Object,
          require: true,
        }
    }
    
}
</script>

<style scoped lang="scss">

.card-wrapper{
    width: calc(88% / 5);
    height: 350px;
    background-color: #2E3A46;
    margin-bottom: 20px;
    padding: 20px;
}

.poster{
  margin: 0 auto;

    img{
        display: block;
        width: 100%;
        margin-bottom: 20px;
    }
}

.album-info {
    text-align: center;
    margin: 0 auto;

    .title{
        text-transform: uppercase;
        font-weight: bold;
        color: white;
        margin-bottom: 15px;
    }

    .author {
      color: #18D860;
    }

    .genre, .year {
        color: #999999;
        margin: 3px;
    }
}

</style>