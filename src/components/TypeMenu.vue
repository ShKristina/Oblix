<template>
  <div class="o-cuisine-container">
    <div
        class="c-cuisine__button"
        v-for="(tab, index) in tabs"
        :key="index"
        :class="['active-menu', { active: this.activeTab === index }]"
        @click="changeMenuTab(index)"
    >
      {{ tab }}
    </div>
  </div>
</template>

<script>
export default {
  name: "TypeMenu",
  data() {
    return {
      activeTab: 0,
    }
  },
  props: {
    tabs: {type: Array, default: () => ([])},
  },
  methods: {
    changeMenuTab(tab) {
      this.activeTab = tab;
      this.$emit('menuButtonChange', tab);
    },
    reset() {
      this.activeTab = 0;
    }
  }
}
</script>