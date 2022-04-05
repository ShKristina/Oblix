<template>
    <div class="head-title">
        <img
            v-if="activeId === 'bar'"
            class="restaurant-image"
            src="../assets/images/Restaurant-and-Bar.jpg"
            alt="Dish picture"
        />
      <img
          v-else-if="activeId==='east'"
          class="restaurant-image"
          src="../assets/images/lunch-zeplin-zip.jpg"
          alt="Dish picture"
      />
      <img
          v-else
          class="restaurant-image"
          src="../assets/images/menus-1.jpg"
          alt="Dish picture"
      />
      <div class="head-title__temp">
        <h1 >{{ temp }}</h1>
      </div>
    </div>
</template>

<script>
export default {
  name: "ImageRestaurant",
  data() {
    return {
      temp: "CHOOSE MENU",
    };
  },
  props: {
    activeId: String
  }
};
</script>

<style lang="sass">

.head-title__temp
  max-width: 1300px
  bottom: 145px
  @media (max-width: 865px)
    bottom: 125px
  position: relative
  height: auto

.head-title
  height: 500px
  @media(max-width: 865px)
    height: 460px
    @media(max-width: 736px)
      height: 340px
  width: 100%
  margin: 0
  padding: 0

.restaurant-image
  width: 100%
  height: 500px
  @media(max-width: 865px)
    height: 460px
    @media(max-width: 737px)
      height: 340px
  position: relative
  object-fit: cover
  filter: brightness(60%)

</style>
