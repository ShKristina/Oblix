<template>
  <div class="o-main-button-container">
    <div class="o-button-container">
      <div
          class="c-button"
          v-for="tab in tabs"
          :key="tab"
          :class="['active-button', { active: currentTab === tab }]"
          @click="changeTab(tab)"
      >
          {{ tab }}
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
  props: {
    tabs: { type:Array, default: () => ([])}
  },
  methods: {
    changeTab(tab) {
      this.currentTab = tab;
      this.$emit('buttonChange', tab);
    }
  }
}
</script>

<style lang="scss">
</style>