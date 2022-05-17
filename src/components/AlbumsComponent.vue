<template>
  <div class="albums">
    <b-container>
      <b-row>
        <slot></slot>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import { BContainer, BRow } from 'bootstrap-vue'

export default {
    name: 'AlbumsComponent',
    components: {
        'b-container': BContainer,
        'b-row': BRow
    }
}
</script>

<style lang="scss" scoped>
  .albums {
    padding-top: 100px;
    background-color: #1e2d3b;
    width: 100vw;
    height: 100vh;

    .album {
      height: 100%;
    }
  }
</style>