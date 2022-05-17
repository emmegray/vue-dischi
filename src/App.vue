<template>
  <div id="app">
    <HeaderComponent></HeaderComponent>
    <AlbumsComponent>
      <!-- Albums -->
      <AlbumComponent 
        img="img"
        title="title song" 
        author="author"
        year="year"
      />
    </AlbumsComponent>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import AlbumsComponent from './components/AlbumsComponent.vue'
import AlbumComponent from './components/AlbumComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    AlbumsComponent,
    AlbumComponent
}
}
</script>

<style lang="scss">
@import "./assets/style/general.scss";
@import "./assets/style/var.scss";

</style>
