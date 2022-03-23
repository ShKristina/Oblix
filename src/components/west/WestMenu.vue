<template>
  <div class="menus-restaurant-main">
    <div class="main-description">
      <div class="description-content"> {{about['west']}}</div>
    </div>
    <div class="panel-menu">
      <div class="panel-menu__cuisine">
        <WestMenuType v-on:westButtonChange="changeMenuWest" />
      </div>

      <div class="panel-menu__menu" v-if="item === 'DESSERTS'">
        <div class="page-logotype">
          <LogoType />
        </div>
        <div class="page-top">
          <h3 class="top-title">desserts</h3>
        </div>
        <div class="page-main" >
          <div class="page-main__item">

            <div class="item">
              <h4>desserts</h4>
              <div v-for="(value) in dataDesserts" :key="value">
                <div v-for="item in value" :key="item" class="item-data">
                  <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>

      <div class="panel-menu__menu" v-else-if="item === 'ROSE BRUNCH'">
        <div class="page-logotype">
          <LogoType />
        </div>
        <div class="page-top">
          <h3 class="top-title">Brunch</h3>
        </div>
        <div class="page-main" >
          <div class="page-main__item">

            <div class="item">
              <h4>rosé brunch 89</h4>
              <div class="item-data2">
                  <div class="item-data__margin">{{brunch['roseBrunch']}}</div>
              </div>
            </div>

            <div class="item">
              <h4>champagne brunch 115</h4>
              <div class="item-data2">
                  <div class="item-data__margin">{{brunch['champagneBrunch']}}</div>
              </div>
            </div>

            <div class="item">
              <h4>starters</h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in brunch['starters']" :key="temp" class="item-data__margin">{{temp}}</div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>sides</h4>
              <div v-for="(value, name) in dataBrunch" :key="value">
                <div v-if="name === 'sides'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

          </div>
        </div>
      </div>

      <div class="panel-menu__menu" v-else>
        <div class="page-logotype">
          <LogoType />
        </div>
        <div class="page-top">
          <h3 class="top-title"> à la carte menu</h3>
        </div>

        <div class="page-main" >
          <div class="page-main__item">

            <div class="item">
              <h4>snacks</h4>
              <div v-for="(value, name) in dataCarte" :key="value">
                <div v-if="name === 'snacks'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>raw bar</h4>
              <div v-for="(value, name) in dataCarte" :key="value">
                <div v-if="name === 'rawbar'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>rotisserie and grill</h4>
              <div v-for="(value, name) in dataCarte" :key="value">
                <div v-if="name === 'rotisserieAndGrill'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>starters</h4>
              <div v-for="(value, name) in dataCarte" :key="value">
                <div v-if="name === 'starters'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>steaks</h4>
              <div v-for="(value, name) in dataCarte" :key="value">
                <div v-if="name === 'steaks'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} </p> <span class="item-price">{{item.price}}</span>
                  </div>
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
  name:'WestMenu',
  components: {},

  data() {
    return {
      carteMenu: [],
      brunch: [],
      desserts:[],
      about:[],
      item:'',
      dataCarte: {},
      dataBrunch:{},
      dataDesserts:{}
    }
  },

  mounted() {
    axios
        .get('http://localhost:3000/WestCarteMenu')
        .then(response => {this.carteMenu = response.data;
          const keys = Object.keys(response.data)
          for(let i = 0; i < keys.length; i+=2){
            this.dataCarte[keys[i]] = this.getCarteMenu(keys[i],keys[i+1])
          }
        })
        .catch(error => console.log(error));
    axios
        .get('http://localhost:3000/WestRoseBrunch')
        .then(response => {this.brunch = response.data;
          const keys = Object.keys(response.data)
          if(keys.length%2){
            keys.shift()
          }
          for(let i = 0; i < keys.length; i+=2){
            this.dataBrunch[keys[i]] = this.getBrunchMenu(keys[i],keys[i+1])
          }
        })
        .catch(error => console.log(error));
    axios
        .get('http://localhost:3000/WestDesserts')
        .then(response => {this.desserts = response.data;
          const keys = Object.keys(response.data)
          for(let i = 0; i < keys.length; i+=2){
            this.dataDesserts[keys[i]] = this.getDessertsMenu(keys[i],keys[i+1])
          }
        })
        .catch(error => console.log(error));
    axios
        .get('http://localhost:3000/aboutRestaurants')
        .then(response => (this.about = response.data))
        .catch(error => console.log(error));
  },

  methods:{
    changeMenuWest(value){
      this.item = value
    },
    getCarteMenu(key, key2){
      let mass = []
      for(let i=0; i < this.carteMenu[key].length; i++) {
        mass.push({title: this.carteMenu[key][i], price: this.carteMenu[key2][i]})
      }
      return mass;
    },

    getBrunchMenu(key, key2){
      let mass = []
      for(let i=0; i < this.brunch[key].length; i++) {
        mass.push({title: this.brunch[key][i], price: this.brunch[key2][i]})
      }
      return mass;
    },

    getDessertsMenu(key, key2){
      let mass = []
      for(let i=0; i < this.desserts[key].length; i++) {
        mass.push({title: this.desserts[key][i], price: this.desserts[key2][i]})
      }
      return mass;
    }
  }
}

</script>