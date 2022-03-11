<template>
  <header>
      <div class="header-container">
          <figure class="logo-wrapper">
              <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Spotify.png/600px-Spotify.png" alt="">
          </figure>
      </div>
  </header>
</template>

<script>

export default {
    name: 'HeaderSpotify',
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
}
    
</style>