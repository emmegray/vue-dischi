<template>
  <div id="app">
    <HeaderComponent></HeaderComponent>
    <AlbumsComponent>
      <!-- Albums -->
      <AlbumComponent
        v-for="album in albums" 
        :key="album.poster"
        :coverUrl="album.poster"
        :title="album.title"
        :author="album.author"
        :year="album.year"
      />
    </AlbumsComponent>
  </div>
</template>

<script>
import axios from "axios";
import HeaderComponent from "./components/HeaderComponent.vue";
import AlbumsComponent from "./components/AlbumsComponent.vue";
import AlbumComponent from "./components/AlbumComponent.vue";

export default {
  name: "App",
  data: () => ({
    albums: []
  }),
  components: {
    HeaderComponent,
    AlbumsComponent,
    AlbumComponent,
  },
  mounted: function ()  {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
      .then(response => response.data)
      .then(json => {
        this.albums = json.response;
      })
  }
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
@import "./assets/style/var.scss";
</style>
