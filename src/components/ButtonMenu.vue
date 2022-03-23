<template>
  <div class="demo">
    <div class="main-container">
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
  <keep-alive>
    <component :is="currentTabComponent"> </component>
  </keep-alive>
</template>



<script>
export default {
  name: "ButtonMenu",
  data() {
    return {
      currentTab: "West",
      tabs: ["West", "East", "Bar"],
    }
  },
  computed: {
    currentTabComponent() {
      return <menuItem temp={this.currentTab.toLowerCase()} />
    }
  },
  methods:{
    changeTab(tab){
      this.currentTab=tab
      this.$emit('buttonChange', tab)
    }
  }

}
</script>




<style lang="sass">

.demo
  display: block
  height: 99px
  @media(max-width: 865px)
    height: 82px
    top: 378px
    @media (max-width: 736px)
      top: 258px
  width: 100%
  margin: 0 auto
  background-color: rgba(20, 9, 6, 0.1)
  top: 401px
  position: absolute

.main-container
  display: flex
  height: 99px
  @media(max-width: 865px)
    height: 82px
  max-width: 1300px


.active-button
  font-weight: bold


.tab-button
  font-weight: 400
  letter-spacing: 1.5px
  line-height: 55px
  margin-right: 59px
  margin-top: 20px
  color: #fff
  cursor: pointer
  top: 50%
  font-family: $font-stack
  font-size: 50px
  @media(max-width: 1055px)
    font-size: 42px
    margin-top: 20px
    @media (max-width: 865px)
      margin-top: 15px
      margin-right: 29px
      @media (max-width: 735px)
        font-size: 38px
        margin-top: 18px

.line
  position: relative
  width: 100%
  height: 4px
  background-color: #fff
  top: 20px
  @media (max-width: 865px)
    top: 8px
    @media (max-width: 735px)
      top: 4px

.lineDisplay
  display: none

</style>