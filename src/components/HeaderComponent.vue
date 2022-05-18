<template>
  <nav class="d-flex flex-wrap align-items-center justify-content-between">
    <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
      <font-awesome-icon transform="grow-5" icon="fa-brands fa-spotify"/>
    </a>
    <slot></slot>
  </nav>
</template>

<script>
export default {
  name: 'HeaderComponent',
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
  padding: 10px;
}

svg {
  color: #1fdf64;
  height: 40px;
  padding: 10px;
}
</style>