<template>
  <div id="home">
    <h1>Films</h1>
    <img v-bind:src="image">
  </div>
</template>

<style lang="scss">
h1 {
  text-align: center;
}
</style>

<script>
// @ is an alias to /src
import Component from "../components/Component.vue";

export default {
  data() {
    return {
      url: null,
      http: "https://image.tmdb.org/t/p/w300/",
      key: "?api_key=05b735a5f79822f887889281f45b295a",
      image: null
    };
  },
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/157336?api_key=05b735a5f79822f887889281f45b295a&append_to_response=videos,images"
      )
      .then(response => (this.url = response.data.poster_path))
      .then(response => (this.image = this.http += this.url += this.key)); //Je concatene les plusieurs parties de l'url pour afficher l'image
  }
};
</script>
