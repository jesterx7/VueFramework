<template>
  <div id="app">
    <navbar-star-wars></navbar-star-wars>
    <logo v-show="detail"></logo>
    <float-button  @all-added="showAll"></float-button>
    <div class="container">
      <transition name="fade">
        <list-characters v-if="detail === true" v-bind="{characters, world}" @charDetails="showCharDetails"></list-characters>
        <detail-characters v-else v-bind="{characterDetails, characterDetailsWorld}"  @back="showBack"></detail-characters>
      </transition>
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
      charAndWorld: {},
      characterDetails: Object,
      characterDetailsWorld: Object,
      detail: true
    }
  },
  methods: {
    showAll(payload1, payload2) {
      this.world = payload1;
      this.characters = payload2;
      this.charAndWorld = {characters: this.characters, world: this.world};
    },
    showCharDetails(payload1, payload2) {
      this.detail = false;
      this.characterDetails = payload1;
      this.characterDetailsWorld = payload2;
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
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
