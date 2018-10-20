<template>
  <div class="fixed-action-btn">
  <a class="btn-floating btn-large red" v-on:click="getCharacters">
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
    }
  },
  methods: {
    getCharacters(){
      axios.get("https://swapi.co/api/people/" + ++this.index)
      .then((response) =>{
        // handle success
        this.characters.push(response.data);
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
    }
  }
};
</script>
<style>
</style>
