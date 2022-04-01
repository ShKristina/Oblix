<template>
    <div class="header">
      <ImageRestaurant :activeId="activeId" />
      <ButtonMenu v-on:buttonChange="changeTab" :tabs="tabs" />
    </div>

    <div class="container">
     <DataMenu :oblix="oblix" :activeId="activeId"/>
    </div>

    <div class="footer">
      <img src="./assets/images/foot.jpg" class="footer-image">
    </div>
</template>

<script>

import axios from "axios";
export default {
  name: 'App',
  data(){
    return{
      activeId:'',
      oblix:{},
      tabs:[],
    }
  },
  methods:{
    changeTab(value){
      this.activeId = value
    },
  },
  mounted() {
    axios
        .get('http://localhost:3000/oblix')
        .then(response => {this.oblix = response.data;
          this.tabs = Object.keys(response.data)
          this.activeId= this.tabs[0]
        })
        .catch(error => console.log(error));
  }
}
</script>

<style lang="scss">

</style>
