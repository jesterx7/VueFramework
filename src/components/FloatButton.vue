<template>
  <div class="fixed-action-btn">
    <transition name="bounce">
      <div v-show="show">
        <p class="One">Click !</p>
      </div>
    </transition>
    <a class="btn-floating btn-large red" v-on:click="getCharacters" @click="show = false">
      <i class="large material-icons">add</i>
    </a>
</div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      characters: [],
      index: 0,
      world: [],
      show: true
    }
  },
  methods: {
    getCharacters(){
      axios.get("https://swapi.co/api/people/" + ++this.index)
      .then((response) =>{
        // handle success
        this.characters.push(response.data);
        axios.get(response.data.homeworld)
          .then(res => {
            // handle success
            this.world.push(res.data);
            console.log(this.world);
            this.$emit('world-added', this.world);
          })
          .catch(error => {
            // handle error
            console.log(error);
          })
          .then(() => {
            // always executed
          });
        console.log(this.characters);
        this.$emit('character-added', this.characters);
      })
      .catch((error) => {
        // handle error
        console.log(error);
      })
      .then(() => {
        // always executed
      });
    },
  }
};
</script>
<style>
@import url(https://fonts.googleapis.com/css?family=Chakra+Petch|Roboto|Roboto+Condensed|Roboto+Slab);
  .bounce-leave-active {
    animation: bounce-in .5s reverse;
  }
  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }

  .One {
    font-weight: bold;
    font-size: 20px;
    margin-bottom: 0px;
    font-family: "Roboto Condensed", sans-serif;
    text-align: center;
  }
</style>
