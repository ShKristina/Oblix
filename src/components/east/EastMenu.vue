<template >
  <div class="menus-restaurant-main">
    <div class="main-description">
    <div class="description-content"> {{about['east']}}</div>
    </div>

    <div class="panel-menu">
      <div class="panel-menu__cuisine">
        <EastMenuType v-on:eastButtonChange="changeMenuEast" />
      </div>

      <div class="panel-menu__menu" v-if="item==='OBLIX EASY'">
        <div class="page-logotype">
          <LogoType/>
        </div>
        <div class="page-top">
          <h3 class="top-title"> oblix easy</h3>
        </div>

        <div class="page-main" >
          <div class="page-main__item">

            <div class="item">
              <h4>Starters</h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in easy['starters']" :key="temp" class="item-data__margin">{{temp}}</div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>Mains</h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in easy['mains']" :key="temp" class="item-data__margin">{{temp}}</div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>Desserts</h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in easy['desserts']" :key="temp" class="item-data__margin">{{temp}}</div>
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
          <h3 class="top-title"> afternoon tea</h3>
        </div>

        <div class="page-main" >
          <div class="page-main__item">

            <div class="item">
              <h4>Sandwiches</h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in tea['sandwiches']" :key="temp" class="item-data__margin">{{temp}}</div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>Pastries</h4>
              <div class="item-data2">
                <div>
                  <div v-for="temp in tea['pastries']" :key="temp" class="item-data__margin">{{temp}}</div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>Scones</h4>
              <div class="item-data2">
                <div >
                  <div v-for="temp in tea['scones']" :key="temp" class="item-data__margin">{{temp}}</div>
                </div>
              </div>
            </div>

            <div class="item">
              <h4>Tea</h4>
              <div v-for="(value, name) in dataTea" :key="value">
                <div v-if="name === 'tea'" >
                  <div v-for="item in value" :key="item" class="item-data">
                    <p> {{item.title}} <span class="item-description">{{item.price}}</span> </p>
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
  name:'EastMenu',

  data() {
    return {
      easy: [],
      tea: [],
      about:[],
      item:'',
      dataTea:{}
    }
  },

  mounted() {
    axios
        .get('http://localhost:3000/EastOblixEasy')
        .then(response => (this.easy = response.data))
        .catch(error => console.log(error));
    axios
        .get('http://localhost:3000/EastAfternoonTea')
        .then(response => {this.tea = response.data;
          const keys = Object.keys(response.data)
          if(keys.length%2){
            keys.shift()
          }
          for(let i = 0; i < keys.length; i+=2){
            this.dataTea[keys[i]] = this.getData(keys[i],keys[i+1])
          }
        })
        .catch(error => console.log(error));
    axios
        .get('http://localhost:3000/aboutRestaurants')
        .then(response => (this.about = response.data))
        .catch(error => console.log(error));
  },

  methods:{
    changeMenuEast(value){
      this.item = value
    },

    getData(key, key2){
      let mass = []
      for(let i=0; i < this.tea[key].length; i++) {
        mass.push({title: this.tea[key][i], price: this.tea[key2][i]})
      }
      return mass;
    }
  }
}


</script>

<style lang="scss">

</style>