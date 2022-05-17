<template>
  <b-col lg="2">
      <div class="album">
          <img :src="coverUrl" :alt="title">
          <h3>{{title}}</h3>
          <h4>{{author}}</h4>
          <h5>{{year}}</h5>
      </div>
  </b-col>
</template>

<script>
import {
    BCol
} from 'bootstrap-vue'

export default {
    name: 'AlbumComponent',
    components: {
        'b-col': BCol
    },
    props: {
        coverUrl: String,
        title: String,
        author: String,
        year: String,
    }
}
</script>

<style lang="scss" scoped>
.album {
    background-color: #2e3a46;
    color: white;
}
</style>