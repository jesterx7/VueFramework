<template>
  <div id="app">
    <navbar-star-wars></navbar-star-wars>
    <float-button @character-added="showCharacters"></float-button>
    <div class="container">
      <list-characters v-bind:characters="characters"></list-characters>
    </div>
  </div>
</template>

<script>
import NavbarStarWars from "./components/NavbarStarWars";
import FloatButton from "./components/FloatButton";
import ListCharacters from "./components/ListCharacters";

export default {
  name: "App",
  components: {
    NavbarStarWars, FloatButton, ListCharacters
  },
  data() {
    return {
      characters: []
    }
  },
  methods: {
    showCharacters(payload) {
      this.characters = payload;
    }
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
