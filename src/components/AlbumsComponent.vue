<template>
  <div class="albums">
    <b-container>
      <slot></slot>
    </b-container>
  </div>
</template>

<script>
import { BContainer } from 'bootstrap-vue'

export default {
    name: 'AlbumsComponent',
    components: {
        'b-container': BContainer
    }
}
</script>

<style lang="scss" scoped>
  .albums {
    padding-top: 100px;
    background-color: #1e2d3b;
    width: 100vw;
    height: 100vh;
  }
</style>