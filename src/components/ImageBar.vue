<template>
  <div class="head-title">
    <img
        class="restaurant-image"
        src="../assets/images/Restaurant-and-Bar.jpg"
        alt="Dish picture"
    />
    <div class="head-title__temp">
      <h1 >{{ temp }}</h1>
    </div>
  </div>

</template>

<script>
export default {
  name:"ImageBar",
  data() {
    return {
      temp: "CHOOSE MENU",
    };
  },
}

</script>