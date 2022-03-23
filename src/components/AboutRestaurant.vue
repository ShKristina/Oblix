<template>
  <div>
  </div>
</template>

<script>


import axios from "axios";

export default {
  name: "AboutRestaurant",
  data(){
    return{
      about:''
    }
  },
  mounted() {
    axios
        .get('http://localhost:3000/aboutRestaurants')
        .then(response => (this.about = response.data))
        .catch(error => console.log(error));
  },


};
</script>

