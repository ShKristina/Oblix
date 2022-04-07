<template>
  <div class="v-button-menu">
    <div class="v-button-menu__wrapper o-main-container">
      <div
          class="v-button-menu__button"
          v-for="tab in tabs"
          :key="tab"
          :class="[{ 'v-button-menu__button--active': currentTab === tab }]"
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
.v-button-menu {
  background-color: rgba(20, 9, 6, 0.1);
  display: block;
  height: 99px;
  left: 0;
  position: absolute;
  right: 0;
  top: 401px;

  @media screen and (max-width: 865px) {
    height: 82px;
    top: 378px;
    
    @media screen and (max-width: 736px) {
      top: 258px
    }
  }

  &__wrapper {
    display: flex;
    height: 99px;

    @media screen and (max-width: 865px) {
      height: 82px;
    }
  }

  .v-button-menu__button {
    color: $primary-color;
    cursor: pointer;
    font-family: $font-stack;
    font-size: 50px;
    font-weight: 400;
    letter-spacing: 1.5px;
    line-height: 55px;
    margin-right: 59px;
    margin-top: 20px;
    text-transform: capitalize;
    top: 50%;

    @media screen and (max-width: 1055px) {
      font-size: 42px;
      margin-top: 20px;

      @media screen and (max-width: 865px) {
        margin-top: 15px;
        margin-right: 29px;

        @media screen and (max-width: 735px) {
          font-size: 38px;
          margin-top: 18px;

          @media screen and (max-width: 320px) {
            font-size: 28px;
            margin-right: 20px;
          }
        }
      }
    }

    &--active {
      font-weight: bold;
      border-bottom: $primary-color;
      border-bottom-width: 4px;
      border-bottom-style: solid;
    }
  }
}
</style>