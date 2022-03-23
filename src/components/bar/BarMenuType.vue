<template>
    <div class="cuisine">
      <div
          class="cuisine__button"
          :class="['active-menu', { active: this.menuBar }]"
          @click="changeMenuBar(tab)"
      > {{ menuBar }}
      </div>
    </div>
</template>

<script>
export default {
  name: "BarMenuType",
  data() {
    return {
      menuBar: "BAR MENU",
    }
  },
  methods:{
    changeMenuBar(tab){
      this.$emit('barButtonChange', tab)
    },
  }
}

</script>

