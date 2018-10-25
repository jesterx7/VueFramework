<template>
  <div id="app">
    <navbar-star-wars></navbar-star-wars>
    <logo v-show="detail"></logo>
    <float-button @character-added="showCharacters" @world-added="showWorld"></float-button>
    <div class="container">
      <list-characters v-if="detail === true" v-bind:world="world" v-bind:characters="characters" @character="showCharacterDetails" @worlds="showDetailWorld"></list-characters>
      <detail-characters v-else :characterDetails="characterDetails" :characterDetailsWorld="characterDetailsWorld" @back="showBack"></detail-characters>
    </div>
  </div>
</template>

<script>
import NavbarStarWars from "./components/NavbarStarWars";
import FloatButton from "./components/FloatButton";
import ListCharacters from "./components/ListCharacters";
import Logo from "./components/Logo";
import DetailCharacters from "./components/DetailCharacters";

export default {
  name: "App",
  components: {
    NavbarStarWars, FloatButton, ListCharacters, Logo, DetailCharacters
  },
  data() {
    return {
      characters: [],
      world: [],
      characterDetails: Object,
      characterDetailsWorld: Object,
      detail: true
    }
  },
  methods: {
    showCharacters(payload) {
      this.characters = payload;
    },
    showWorld(payload) {
      this.world = payload;
    },
    showCharacterDetails(payload) {
      this.detail = false;
      this.characterDetails = payload;
    },
    showDetailWorld(payload) {
      this.characterDetailsWorld = payload;
    },
    showBack(payload) {
      this.detail = payload;
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
