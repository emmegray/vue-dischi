<template>
  <nav class="d-flex flex-wrap align-items-center justify-content-between">
    <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
      <font-awesome-icon transform="grow-5" icon="fa-brands fa-spotify"/>
    </a>
    <b-dropdown text="Seleziona un genere">
      <b-dropdown-item >genere</b-dropdown-item>
    </b-dropdown>
  </nav>
</template>

<script>
import { BDropdown, BDropdownItem } from 'bootstrap-vue'
export default {
  name: 'HeaderComponent',
  components: {
    "b-dropdown": BDropdown,
    "b-dropdown-item": BDropdownItem
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
@import "../assets/style/var.scss";

nav {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: $bg-lightblue;
}

svg {
  color: #1fdf64;
  height: 40px;
  padding: 10px;
}


</style>