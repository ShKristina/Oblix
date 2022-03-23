<template>
    <div class="header">
      <div v-if="item ==='East'">
        <ImageEast />
      </div>
      <div v-else-if="item === 'Bar'">
        <ImageBar />
      </div>
      <div v-else>
        <ImageWest />
      </div>
      <ButtonMenu v-on:buttonChange="changeTab" />
    </div>

    <div class="container">
      <div v-if="item==='Bar'">
        <BarMenu /> </div>
      <div v-else-if="item==='East'">
        <EastMenu /> </div>
      <div v-else>
        <WestMenu /> </div>
    </div>

    <div class="footer">
      <img src="./assets/images/foot.jpg" class="footer-image">
    </div>


</template>

<script>



export default {
  name: 'App',

  data(){
    return{
      item:'',
    }
  },
  methods:{
    changeTab(value){
      this.item = value
    },
  }

}
</script>

<style lang="scss">


</style>
