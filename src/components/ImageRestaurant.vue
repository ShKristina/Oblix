<template>
    <div class="v-image-restaurant">
        <img
            v-if="activeId === 'bar'"
            class="v-image-restaurant__image o-header"
            src="../assets/images/Restaurant-and-Bar.jpg"
            alt="Dish picture"
        />
      <img
          v-else-if="activeId==='east'"
          class="v-image-restaurant__image"
          src="../assets/images/lunch-zeplin-zip.jpg"
          alt="Dish picture"
      />
      <img
          v-else
          class="v-image-restaurant__image"
          src="../assets/images/menus-1.jpg"
          alt="Dish picture"
      />
      <div class="v-image-restaurant__title o-main-container o-header">
        <h1 >{{ title }}</h1>
      </div>
    </div>
</template>

<script>
export default {
  name: "ImageRestaurant",
  data() {
    return {
      title: "CHOOSE MENU",
    };
  },
  props: {
    activeId: String
  }
};
</script>

<style lang="scss">
.v-image-restaurant {
  height: 500px;

  @media(max-width: 865px) {
    height: 460px;

    @media(max-width: 736px) {
      height: 340px
    }
  }

  &__image {
    width: $full-width;
    height: 500px;
    object-fit: cover;
    filter: brightness(60%);

    @media(max-width: 865px) {
      height: 460px;

      @media(max-width: 737px) {
        height: 340px
      }
    }
  }

  &__title {
    bottom: 145px;

    @media (max-width: 865px) {
      bottom: 125px
    }
  }
}
</style>
