<template>
  <b-col lg="2">
    <div class="album">
      <img :src="coverUrl" :alt="title" />
      <h3>{{ title }}</h3>
      <h4>{{ author }}</h4>
      <h5>{{ year }}</h5>
    </div>
  </b-col>
</template>

<script>
import { BCol } from "bootstrap-vue";

export default {
  name: "AlbumComponent",
  components: {
    "b-col": BCol,
  },
  props: {
    coverUrl: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/general.scss";
@import "../assets/style/var.scss";

.album {
  background-color: $bg-lightblue ;
  color: white;
  text-align: center;
  padding: 1rem;
  padding-bottom: 3rem;
}

img {
  margin-bottom: 1rem;
}

h3 {
  font-size: 1rem;
  font-variant: small-caps;
  text-transform: lowercase;
  margin-bottom: 1rem;
}

h4,
h5 {
  color: gray;
  font-size: 0.9rem;
}
</style>