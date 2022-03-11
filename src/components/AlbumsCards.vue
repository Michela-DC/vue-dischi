<template>
    <li class="card-wrapper">

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
      
    </li>
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

@import '../assets/scss/common.scss';

.card-wrapper{
    width: calc(88% / 5);
    background-color: rgba(white, 0.1);; 
    padding: 15px;
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

    .author, .genre, .year{
        margin-bottom: 5px;
    }

    .author {
      color: #18D860;
    }

    .genre, .year {
        color: #999999;
        font-size: 14px;
    }
}

</style>