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

<style lang="scss">


</style>
