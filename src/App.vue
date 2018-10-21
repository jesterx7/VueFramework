<template>
  <div id="app">
    <navbar-star-wars></navbar-star-wars>
    <logo></logo>
    <float-button @character-added="showCharacters" @world-added="showWorld"></float-button>
    <div class="container">
      <list-characters v-bind:characters="characters" v-bind:world="world"></list-characters>
    </div>
  </div>
</template>

<script>
import NavbarStarWars from "./components/NavbarStarWars";
import FloatButton from "./components/FloatButton";
import ListCharacters from "./components/ListCharacters";
import Logo from "./components/Logo";

export default {
  name: "App",
  components: {
    NavbarStarWars, FloatButton, ListCharacters, Logo
  },
  data() {
    return {
      characters: [],
      world: []
    }
  },
  methods: {
    showCharacters(payload) {
      this.characters = payload;
    },
    showWorld(payload) {
      this.world = payload;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
}
</style>
