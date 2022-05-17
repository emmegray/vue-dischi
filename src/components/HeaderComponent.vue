<template>
  <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
    <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
      <font-awesome-icon icon="fa-brands fa-spotify"/>
    </a>

    <div class="text-end">
      <form class="col-12 col-lg-auto mb-3 mb-lg-0 me-lg-3">
        <input type="search" class="form-control form-control-dark" placeholder="Search..." aria-label="Search">
      </form>
    </div>
  </div>
</template>

<script>
export default {
name: 'HeaderComponent'
}
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
@import "../assets/style/var.scss";

i {
  color: #1fdf64;
  font-size: large;
}


</style>