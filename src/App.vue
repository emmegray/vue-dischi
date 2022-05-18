<template>
  <div id="app">
    <HeaderComponent>
      <SearchBarComponent 
        :genres="genres" 
        @searchGenre="selectGenre"
        :authors="authors"
        @searchAuthor="selectAuthor"
      />
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

    <b-container class="not_found" v-if="albums.length > 0 && selectedAlbums.length === 0">
      <h2>Non ci sono album corrispondenti</h2>
    </b-container>
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
    selectedAuthor: "",
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
    },
    selectAuthor(author){
      this.selectedAuthor = author
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
    authors(){
      let authorsFound = [];
      this.albums.forEach(
        album => {
          if (authorsFound.includes(album.author)) return;
          authorsFound.push(album.author)
        }
      );
      return authorsFound;
    },
    selectedAlbums(){      
      return this.albums.filter(
        album => {
          let showAlbum = true;

          if (this.selectedGenre) {
              if (this.selectedGenre !== album.genre) {
                showAlbum = false;
              }
          }

          if (this.selectedAuthor) {
              if (this.selectedAuthor !== album.author) {
                showAlbum = false;
              }
          }

          return showAlbum;
        }
      )
    },
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

.not_found {
  color: white;
  text-align: center;
}
</style>
