<template>
  <b-dropdown
    @keyup.enter="$emit('search', genreSearch)"
    text="Generi"
  >
    <b-dropdown-item
      value=""
      @click="emitGenre('')">Tutti i generi</b-dropdown-item>
    <b-dropdown-item
      v-for="genre in genres"
      :key="genre"
      :value="genre"
      @click="emitGenre(genre)">{{ genre }}</b-dropdown-item
    >
  </b-dropdown>
</template>

<script>
import { BDropdown, BDropdownItem } from "bootstrap-vue";
export default {
  name: "SearchBarComponent",
  components: {
    "b-dropdown": BDropdown,
    "b-dropdown-item": BDropdownItem,
  },
  props: {
    genres: Array,
  },
  data() {
    return {
      genreSearch: "",
    };
  },
  methods: {
    emitGenre(genre){
      this.$emit('search', genre);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
@import "../assets/style/var.scss";
</style>