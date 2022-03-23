<template >
  <div class="menus-restaurant-main">
    <div class="main-description">
      <div class="description-content"> {{about['bar']}}</div>
    </div>

    <div class="panel-menu">
      <div class="panel-menu__cuisine">
        <BarMenuType v-on:barButtonChange="changeMenuBar"/>
      </div>

      <div class="panel-menu__menu">
        <div class="page-logotype">
          <LogoType />
        </div>
        <div class="page-top">
          <h3 class="top-title"> Bar Menu</h3>
        </div>

        <div class="page-main" >
          <div class="page-main__item">

            <div class="item">
              <h4>beers</h4>
              <div v-for="(value, name) in menu" :key="value">
                <div v-if="name === 'beers'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>Champagne (150ml 750ml)</h4>
              <div v-for="(value, name) in menu" :key="value">
                <div v-if="name === 'champagne'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>COCKTAILS</h4>
              <div v-for="(value, name) in menu" :key="value">
                <div v-if="name === 'cocktails'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>desserts <span class="item-price2">15</span></h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in bar['desserts']" :key="temp">{{temp}}</div>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>
    </div>
  </div>

</template>


<script>
import axios from "axios";

export default {
  name:'BarMenu',
  data() {
    return {
      keys:[],
      bar: [],
      about:[],
      item:'',
      menu: {}
    }
  },

  mounted() {
    axios
        .get('http://localhost:3000/BarMenu')
        .then(response => {this.bar = response.data;
          const keys = Object.keys(response.data)
          if(keys.length%2){
            keys.pop()
          }
          for(let i = 0; i < keys.length; i+=2){
            this.menu[keys[i]] = this.getData(keys[i],keys[i+1])
          }
        })
        .catch(error => console.log(error));
    axios
        .get('http://localhost:3000/aboutRestaurants')
        .then(response => (this.about = response.data))
        .catch(error => console.log(error));
  },

  methods:{
    changeMenuBar(value){
      this.item = value
    },

    getData(key, key2){
      let mass = []
      for(let i=0; i < this.bar[key].length; i++) {
        mass.push({title: this.bar[key][i], price: this.bar[key2][i]})
      }
      return mass;
    }
  }
}


</script>
