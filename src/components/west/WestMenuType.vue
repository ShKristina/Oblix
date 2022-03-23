<template>
    <div class="cuisine">
      <div
          class="cuisine__button"
          v-for="tab in tabs"
          :key="tab"
          :class="['active-menu', { active: this.menuWest === tab }]"
          @click="changeMenuWest(tab)"
      >
          {{ tab }}
      </div>
      <keep-alive>
        <component  :is="currentWestComponent"> </component>
      </keep-alive>
    </div>

</template>

<script>
export default {
  name: "WestMenuType",
  data() {
    return {
      menuWest: "À LA CARTE MENU",
      tabs: ["À LA CARTE MENU", "ROSE BRUNCH", "DESSERTS"]
    }
  },
  computed: {
    currentWestComponent() {
      return <menuItem data={this.menuWest.toLowerCase()} />
    }
  },
  methods:{
    changeMenuWest(tab){
      this.menuWest=tab
      this.$emit('westButtonChange', tab)
    }
  }

}

</script>