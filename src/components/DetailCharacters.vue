<template>
  <div class="container">
    <div class="contain"> 
      <img class="profile circle" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTI5TDjHkXbNGlduL7AEVMwGn4bc-QosNt7IRcp9fBJ4qN6N0pmHg">
    </div>
    <table>
      <th>Abc</th>
    </table>
    <button>Back</button>
  </div>
</template>

<script>
export default {
  props: {
    characterDetails: Array
  }
};
</script>

<style>
.contain {
  text-align: center;
}

.profile {
  margin-top: 30px;
  height: 100px;
  text-align: center;
}
</style>
