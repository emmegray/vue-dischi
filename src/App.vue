<template>
  <div id="app">
    <HeaderComponent>
      <SearchBarComponent :genres="genres" @search="selectGenre" />
    </HeaderComponent>

    <LoaderComponent v-if="albums.length === 0"></LoaderComponent>

    <AlbumsComponent v-if="albums.length > 0">
      <!-- Albums -->
      <AlbumComponent
        v-for="album in selectedAlbums"
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
import LoaderComponent from "./components/LoaderComponent.vue";
import SearchBarComponent from "./components/SearchBarComponent.vue"

export default {
  name: "App",
  data: () => ({
    albums: [],
    selectedGenre: "",
  }),
  components: {
    HeaderComponent,
    AlbumsComponent,
    AlbumComponent,
    LoaderComponent,
    SearchBarComponent
  },
  methods: {
    selectGenre(genre){
      this.selectedGenre = genre
    }
  },
  mounted: function ()  {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
      .then(response => response.data)
      .then(json => {
        this.albums = json.response;
      })
  },
  computed: {
    genres() {
      let genresFound = [];
      this.albums.forEach(
        album => {
          if (genresFound.includes(album.genre)) return;
          genresFound.push(album.genre)
        }
      );
      return genresFound;
    },
    selectedAlbums(){
      if (this.selectedGenre === '') return this.albums
      
      return this.albums.filter(
        album => this.selectedGenre === album.genre
      )
    }
  }
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";
@import "./assets/style/var.scss";

#app {
  background-color: $bg-dark;
  height: 100vh;
  width: 100vw;
}
</style>
