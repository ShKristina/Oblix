<template>
  <div class="o-btn-container">
    <button
        class="c-btn"
        v-for="(tab, index) in tabs"
        :key="index"
        :class="[{ 'c-btn--active': this.activeTab === index }]"
        @click="changeMenuTab(index)"
    >
      {{ tab }}
    </button>
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