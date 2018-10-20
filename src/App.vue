<template>
  <div id="app">
    <navbar-star-wars></navbar-star-wars>
    <float-button></float-button>
  </div>
</template>

<script>
import NavbarStarWars from "./components/NavbarStarWars";
import FloatButton from "./components/FloatButton";

export default {
  name: "App",
  components: {
    NavbarStarWars, FloatButton
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  position: relative;
}
</style>
