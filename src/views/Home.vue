<template>
  <div id="home">
    <h1>Films</h1>
    <div class="img__container">
      <div>
        <h2>{{ title() }}</h2>
        <img v-bind:src="image" alt @click="details()">
        <p>{{ caption }}</p>
      </div>
      <div>
        <h2>{{ title() }}</h2>
        <img v-bind:src="image" alt @click="details()">
        <p>{{ caption }}</p>
      </div>
      <div>
        <h2>{{ title() }}</h2>
        <img v-bind:src="image" alt @click="details()">
        <p>{{ caption }}</p>
      </div>
    </div>
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
      key: "?api_key=05b735a5f79822f887889281f45b295a",
      image: null,
      name: "",
      caption: "",
      randomId: ""
    };
  },
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/now_playing?api_key=05b735a5f79822f887889281f45b295a&language=en-US&page=1"
      )
      .then(response => (this.url = response.data.results[0].poster_path))
      .then(response => (this.image = this.http += this.url += this.key)); //Je concatene les plusieurs parties de l'url pour afficher l'image
  },
  methods: {
    randomNumber() {
      this.randomId = Math.floor(Math.random() * (10 - 1 + 1)) + 1;
    },
    details() {
      axios
        .get(
          "https://api.themoviedb.org/3/movie/now_playing?api_key=05b735a5f79822f887889281f45b295a&language=en-US&page=1"
        )
        .then(response => (this.caption = response.data.results[0].overview))
        .then(response => console.log(this.caption));
      console.log(randomId);
    },
    title() {
      axios
        .get(
          "https://api.themoviedb.org/3/movie/now_playing?api_key=05b735a5f79822f887889281f45b295a&language=en-US&page=1"
        )
        .then(response => (this.name = response.data.results[0].title));
      return this.name;
    }
  }
};
</script>
