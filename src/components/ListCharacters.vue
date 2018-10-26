<template>
<div class="container">
  <div class="search-wrapper">
      <input type="text" v-model="search" placeholder="Search Cast.."/>
  </div>
  <ul class="collection">
    <li class="collection-item avatar" v-for="(characters, index) in charactersList" :key="index">
      <img v-if="getGender(index) === 'male'" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTI5TDjHkXbNGlduL7AEVMwGn4bc-QosNt7IRcp9fBJ4qN6N0pmHg" alt="" class="circle">
      <img v-else-if="getGender(index) === 'female'"  alt="" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSNngF0RFPjyGl4ybo78-XYxxeap88Nvsyj1_txm6L4eheH8ZBu" class="circle">
      <img v-else src="https://marketplace.canva.com/MAB6v3AfpmA/1/thumbnail/canva-robot-MAB6v3AfpmA.png" class="circle">
      <span class="title">{{characters.name}}</span>
      <br>
      <span>World {{world[index].name}}</span>
      <br>
      <button class="btnDetail" @click="getDetails(characters, index)">View Details</button>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  data() {
    return {
      search: "",
    }
  },
  props: {
    characters : Array,
    world : Array
  },
  methods: {
    getGender(index) {
      return this.characters[index].gender;
    },
    getDetails(character, index) {
      this.$emit("charDetails", character, this.world[index]);
    }
  },
  computed: {
    charactersList() {
      return this.characters.filter(characters => {
        return characters.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
};
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Chakra+Petch|Roboto|Roboto+Condensed|Roboto+Slab);

.collection {
  border: none;
}

.title {
  font-weight: bold;
  font-family: 'Roboto Slab', sans-serif;
}

.btnDetail {
  background: #5788d6;
  color: white;
  border-radius: 5px;
  border: 0px;
}
</style>
