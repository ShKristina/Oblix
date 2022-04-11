<template>
  <div class="o-restaurant-wrapper o-main-container">
    <div class="v-main-description">
      <div class="v-main-description__content"  v-if="!!activeId">
        {{oblix[activeId].description}}
      </div>
    </div>

    <TypeMenu v-on:menuButtonChange="changeMenuTab" :tabs="tabs" ref="typeMenu"/>

    <div class="v-menu-page" >
      <LogoType />
      <div v-if="!!Object.keys(cuisineItems).length">
        <MenuItem :cuisineItems="cuisineItems"/>
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

<style lang="scss">
.o-restaurant-wrapper {
  padding-top: 30px;
  padding-bottom: 20px;

  @media screen and (min-width: 865px) {
    padding-top: 70px;
    padding-bottom: 91px;
  }

  .v-main-description {
    margin-bottom: 40px;

    @media screen and (min-width: 865px) {
      margin-bottom: 70px;
    }

    &__content {
      padding-bottom: 24px;
      letter-spacing: .023em;
      line-height: 1.5em;
      font-size: 18px;

      @media screen and (min-width: 865px) {
        width: 745px;
        font-size: 21px;
      }
    }
  }

  .v-menu-page {
    background-color: $white-color;
    padding: 70px;
    padding-top: 48px;

    @media screen and (max-width: 737px) {
      padding: 20px;
      padding-bottom: 30px;
    }
  }
}
</style>
