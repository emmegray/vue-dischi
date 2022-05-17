<template>
  <div id="app">
    <HeaderComponent></HeaderComponent>
    <AlbumsComponent>
      <!-- Albums -->
      <AlbumComponent 
        img="oooo"
        title="aaaa" 
        author="bbb"
        year="ccc"
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
