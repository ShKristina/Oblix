<template>
  <div class="menus-restaurant-main">
    <div class="main-description">
      <div class="description-content"  v-if="!!activeId">
        {{oblix[activeId].description}}
      </div>
    </div>
    <div class="panel-menu">
      <div class="panel-menu__cuisine">
        <TypeMenu v-on:menuButtonChange="changeMenuTab" :tabs="tabs" ref="typeMenu"/>
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
  data() {
    return {
      cuisineItems: {},
      tabs: [],
    }
  },
  props: ['oblix', 'activeId'],
  watch: {
    activeId: function (newVal) {
      this.setData(newVal);
      this.$refs.typeMenu.reset();
    }
  },
  methods: {
    changeMenuTab(value) {
      this.cuisineItems=this.oblix[this.activeId].cuisines[value];
    },
    setData(newVal) {
      this.tabs = this.oblix[newVal].cuisines.map(item => item.сuisine_title);
      this.changeMenuTab(0);
    }
  }
}
</script>

<style>
</style>