<template>
  <div class="page-top">
    <div  v-for="(item, value) in cuisineItems" :key="item">
      <div v-if="value==='сuisine_title_menu'">
      <h3 class="top-title">{{item}}</h3>
      </div>
    </div>
  </div>

  <div class="page-main" >
    <div class="page-main__item">
      <div  v-for="name in cuisineItems.menu_items" :key="name">
        <div class="item">
          <h4>{{name.item_text}} <span class="item-price__title"> {{name.item_price}}</span></h4>
          <div v-for="item in name.dish_items" :key="item" class="item-data">
            <p>{{item.item_text}} <span class="item-description">{{item.item_addition}}</span> </p>
            <span class="item-price">{{item.item_price}}</span>
          </div>
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
