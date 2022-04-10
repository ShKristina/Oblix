<template>
  <div class="v-button-menu">
    <div class="v-button-menu__wrapper o-main-container">
      <button
          class="v-button-menu__button"
          v-for="tab in tabs"
          :key="tab"
          :class="[{ 'v-button-menu__button--active': currentTab === tab }]"
          @click="changeTab(tab)"
      >
        {{ tab }}
      </button>
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
    tabs: {type: Array, default: () => ([])}
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
.v-button-menu {
  background-color: rgba(20, 9, 6, 0.1);
  display: block;
  height: 82px;
  left: 0;
  position: absolute;
  right: 0;
  bottom: 0;

  @media screen and (min-width: 865px) {
    height: 99px;
  }

  &__wrapper {
    display: flex;
    height: 99px;

    @media screen and (max-width: 865px) {
      height: 82px;
    }
  }

  .v-button-menu__button {
    color: $white-color;
    cursor: pointer;
    font-family: $font-stack;
    font-size: 50px;
    letter-spacing: 1.5px;
    margin-right: 59px;
    text-transform: capitalize;
    background-color: inherit;
    border: none;
    padding: 0;

    @media screen and (max-width: 1055px) {
      font-size: 42px;

      @media screen and (max-width: 865px) {
        margin-right: 29px;

        @media screen and (max-width: 735px) {
          font-size: 38px;

          @media screen and (max-width: 320px) {
            font-size: 28px;
            margin-right: 20px;
          }
        }
      }
    }

    &--active {
      font-weight: bold;
      border-bottom: $white-color;
      border-bottom-width: 4px;
      border-bottom-style: solid;
    }
  }
}
</style>