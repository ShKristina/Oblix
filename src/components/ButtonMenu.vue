<template>
  <div class="demo">
    <div class="main-container" >
      <div
          class="tab-button"
          v-for="tab in tabs"
          :key="tab"
          :class="['active-button', { active: currentTab === tab }]"
          @click="changeTab(tab)"
      >
          {{ tab }}
        <div :class="['line', currentTab !== tab && 'lineDisplay']" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ButtonMenu",
  data() {
    return {
      currentTab: 'west'
    }
  },
  props:{
    tabs: {type:Array, default: () => ([])}
  },
  methods:{
    changeTab(tab){
      this.currentTab=tab
      this.$emit('buttonChange', tab)
    },
    setActiveTab(){
      this.currentTab = this.tabs.length ? this.tabs[0] : ''
    }
  }
}
</script>




<style lang="scss">
</style>