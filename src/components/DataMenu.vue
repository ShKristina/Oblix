<template>
  <div class="menus-restaurant-main">
    <div class="main-description" >
      <div class="description-content"  v-if="!!activeId"> {{oblix[activeId].description}}</div>
    </div>
    <div class="panel-menu">
      <div class="panel-menu__cuisine">
        <TypeMenu v-on:menuButtonChange="changeMenuTab" :tabs="tabs" />
      </div>

      <div class="panel-menu__menu" >
        <div class="page-logotype">
          <LogoType />
        </div>
        <div v-if="!!Object.keys(cuisineItems).length">
          <MenuItem :cuisineItems="cuisineItems"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'DataMenu',
  data(){
    return{
      oblixMenuItem: 0,
      cuisineItems:{},
      tabs:[],
    }
  },
  props:['oblix', 'activeId'],
  watch:{
    oblix: function (newVal, oldVal) {
      this.setData()
      console.log(oldVal, newVal)
    },
    activeId: function (newVal, oldVal) {
      console.log(oldVal, newVal)
    }
  },
  methods:{
    changeMenuTab(value){
      this.oblixMenuItem = value
      this.cuisineItems=this.oblix[this.activeId].cuisines[value]
      console.log(this.cuisineItems, value)
    },
    setData(){
      this.tabs = this.oblix[this.activeId].cuisines.map(item => item.сuisine_title)
      this.changeMenuTab(0)
    }
  }
}
</script>

<style>

</style>