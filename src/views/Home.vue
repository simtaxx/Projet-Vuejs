<template>
  <div id="home">
    <h1>Films</h1>
    <h2>{{ info }}</h2>
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
      info: null
    };
  },
  mounted() {
    axios
      .get(
        "https://image.tmdb.org/t/p/w500/8uO0gUM8aNqYLs1OsTBQiXu0fEv.jpg?api_key=05b735a5f79822f887889281f45b295a"
      )
      .then(response => (this.info = response.data))
      .then(response => console.log(this.info));
  }
};
</script>
