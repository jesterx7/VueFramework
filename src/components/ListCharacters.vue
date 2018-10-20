<template>
  <ul class="collection">
    <li class="collection-item avatar" v-for="(characters, index) in characters" :key="index">
      <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTI5TDjHkXbNGlduL7AEVMwGn4bc-QosNt7IRcp9fBJ4qN6N0pmHg" alt="" class="circle">
      <span class="title">{{characters.name}}</span>
      <br>
      <span>{{characters.height}}</span>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    characters: Array
  }
};
</script>

<style>
.collection {
  border: none;
}
</style>
