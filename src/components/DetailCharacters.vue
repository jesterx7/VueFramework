<template>
  <div class="container">
    <div class="contain"> 
      <img v-if="getGender() === 'male'" class="profile circle" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTI5TDjHkXbNGlduL7AEVMwGn4bc-QosNt7IRcp9fBJ4qN6N0pmHg">
      <img v-else-if="getGender() === 'female'"  alt="" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSNngF0RFPjyGl4ybo78-XYxxeap88Nvsyj1_txm6L4eheH8ZBu" class="profile circle">
      <img v-else src="https://marketplace.canva.com/MAB6v3AfpmA/1/thumbnail/canva-robot-MAB6v3AfpmA.png" class="profile circle">      
    </div>
    <table>
      <tr>
        <th>Name</th>
        <td>{{characterDetails.name}}</td> 
      </tr>
      <tr>
        <th>Height</th>
        <td>{{characterDetails.height}}</td> 
      </tr>
      <tr>
        <th>Weight</th>
        <td>{{characterDetails.mass}}</td> 
      </tr>
      <tr>
        <th>Skin Color</th>
        <td>{{characterDetails.skin_color}}</td> 
      </tr>
      <tr>
        <th>Hair Color</th>
        <td>{{characterDetails.hair_color}}</td> 
      </tr>
      <tr>
        <th>Eye Color</th>
        <td>{{characterDetails.eye_color}}</td> 
      </tr>
      <tr>
        <th>Birth Year</th>
        <td>{{characterDetails.birth_year}}</td> 
      </tr>
      <tr>
        <th>Gender</th>
        <td>{{characterDetails.gender}}</td> 
      </tr>
      <tr>
        <th>Home World</th>
        <td>{{characterDetailsWorld.name}}</td> 
      </tr>
    </table>
    <button @click="getBack">Back</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      back: false,
    }
  },
  props: {
    characterDetails: Array,
    characterDetailsWorld : Array
  },
  methods: {
    getBack() {
      this.back = true;
      this.$emit("back", this.back);
    },
    getGender() {
      return this.characterDetails.gender;
    }
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
