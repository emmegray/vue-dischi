<template>
  <div id="Search">
    <b-dropdown @keyup.enter="$emit('search', genreSearch)" :text="labelDropdownGenre">
      <b-dropdown-item value="" @click="emitGenre('')">Tutti i generi</b-dropdown-item>
      <b-dropdown-item
        v-for="genre in genres"
        :key="genre"
        :value="genre"
        @click="emitGenre(genre)"
        >{{ genre }}</b-dropdown-item
      >
    </b-dropdown>

    <b-dropdown @keyup.enter="$emit('search', authorSearch)" :text="labelDropdownAuthor">
      <b-dropdown-item value="" @click="emitAuthor('')">Tutti gli artisti</b-dropdown-item>
      <b-dropdown-item
        v-for="author in authors"
        :key="author"
        :value="author"
        @click="emitAuthor(author)"
        >{{ author }}</b-dropdown-item>
    </b-dropdown>
  </div>

</template>

<script>
import { BDropdown, BDropdownItem } from "bootstrap-vue";
export default {
  name: "SearchBarComponent",
  components: {
    "b-dropdown": BDropdown,
    "b-dropdown-item": BDropdownItem,
  },
  data: () => ({
    selectedGenre: "",
    selectedAuthor: "",
  }),
  props: {
    genres: Array,
    authors: Array,
  },
  methods: {
    emitGenre(genre) {
      this.$emit("searchGenre", genre);
      this.selectedGenre = genre
    },
    emitAuthor(author) {
      this.$emit("searchAuthor", author);
      this.selectedAuthor = author
    },
  },
  computed: {
    labelDropdownGenre() {
      if (this.selectedGenre) return this.selectedGenre
      return "Genere"
    },
    labelDropdownAuthor() {
      if (this.selectedAuthor) return this.selectedAuthor
      return "Artisti"
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
@import "../assets/style/var.scss";
.btn-group {
  padding: 10px;
}
</style>