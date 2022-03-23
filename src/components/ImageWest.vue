<template>
    <div class="head-title">
      <img
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
  name: "ImageWest",
  data() {
    return {
      temp: "CHOOSE MENU",
    };
  },
  props: {
    buttonType: String
  },
  methods:{
    imageChange(){
      console.log(this.buttonType)
    }
  }
};
</script>

<style lang="sass">

h1
  font-family: Muli-ExtraBold
  color: #fff
  font-size: 18px
  @media (max-width: 865px)
    font-size: 16px
  font-weight: 700
  line-height: 1.33em
  margin: 0 0 20px
  opacity: 0.5
  letter-spacing: .03em


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
