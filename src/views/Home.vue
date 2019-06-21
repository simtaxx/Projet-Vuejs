<template>
  <div id="home">
    <h1>Films</h1>
    <ul class="img__container">
      <li v-for="i in this.array">
        <h2>{{ i.title }}</h2>
        <img :src="http + i.poster_path" :alt="i.overview">
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
#home {
  height: 100vh;
}
h1 {
  text-align: center;
  height: 16vh;
}
.img__container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: center;
}
</style>

<script>
// @ is an alias to /src
import Component from "../components/Component.vue";
import game from "../assets/data";

export default {
  data() {
    return {
      url: null,
      http: "https://image.tmdb.org/t/p/w300/",
      array: null,
      name: null
    };
  },
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/now_playing?api_key=05b735a5f79822f887889281f45b295a&language=en-US&page=1"
      )
      .then(response => (this.array = response.data.results))
      .then(response => console.log(this.array));
  }
};
</script>
