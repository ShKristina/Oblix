<template>
  <div class="o-header">
    <ImageRestaurant :activeId="activeId"/>
    <ButtonMenu v-on:buttonChange="changeTab" :tabs="tabs"/>
  </div>

  <div>
    <DataMenu :oblix="oblix" :activeId="activeId"/>
  </div>

  <div>
    <img src="./assets/images/foot.jpg" class="v-footer-image">
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'App',
  data() {
    return{
      activeId: '',
      oblix: {},
      tabs: [],
    }
  },
  methods: {
    changeTab(value) {
      this.activeId = value;
    }
  },
  mounted() {
    axios
        .get('http://localhost:3000/oblix')
        .then(response => {
          this.oblix = response.data;
          this.tabs = Object.keys(response.data);
          this.activeId = this.tabs[0];
        })
        .catch(error => console.log(error));
  }
}
</script>

<style lang="scss">
.v-footer-image {
  height: 280px;
  width: $full-width;
  object-fit: cover;

  @media screen and (max-width: 865px) {
    height: 150px
  }
}
</style>
