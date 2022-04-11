<template>
  <div v-for="(item, value) in cuisineItems" :key="item">
    <div v-if="value==='сuisine_title_menu'" class="v-page-top">
      <h3>{{item}}</h3>
    </div>
  </div>

  <div class="v-page-grid">
    <div v-for="name in cuisineItems.menu_items" :key="name">
      <div class="c-cuisine-item">
        <h4>{{ name.item_text }} <span> {{ name.item_price }}</span></h4>
        <div v-for="item in name.dish_items" :key="item" class="c-cuisine-item__dish">
          <p>{{ item.item_text }} <span>{{ item.item_addition }}</span></p>
          <span class="c-cuisine-item__price">{{ item.item_price }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MenuItem",
  props:{
    cuisineItems: {type:Object, default: () => ({})}
  }
}
</script>

<style lang="scss">
.v-page-top {
  display: flex;
  margin-top: 52px;
  padding-bottom: 73px;
  border-bottom-width: 2px;
  border-bottom-style: solid;
  border-bottom-color: $light-gray-color
}

.v-page-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-column-gap: 70px;

  @media screen and (max-width: 865px) {
    display: flex;
    flex-direction: column;
  }
}
</style>