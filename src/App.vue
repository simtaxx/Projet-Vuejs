<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home |</router-link>
      <router-link to="/page">| page</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
//Reset
body {
  font: 16px sans-serif;
  margin: 0;
}
h1,
h1,
h3,
p,
ul {
  margin: 0;
  padding: 0;
  list-style: none;
  font-weight: 100;
}
* {
  box-sizing: border-box;
}
//Pagination
#nav {
  display: flex;
  flex-direction: row;
  justify-content: center;
  position: absolute;
  margin-left: auto;
  margin-right: auto;
  left: 0;
  right: 0;
  bottom: 0;

  a {
    text-decoration: none;
    color: black;
  }
}
</style>
