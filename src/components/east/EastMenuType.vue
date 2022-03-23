<template>
    <div class="cuisine">
      <div
          class="cuisine__button"
          v-for="tab in tabs"
          :key="tab"
          :class="['active-menu', { active: this.menuEast === tab }]"
          @click="changeMenuEast(tab)"
      >
          {{ tab }}
      </div>
      <keep-alive>
        <component :is="currentEastComponent"> </component>
      </keep-alive>
    </div>
</template>

<script>
export default {
  name: "EastMenuType",
  data() {
    return {
      menuEast: "AFTERNOON TEA",
      tabs: ["AFTERNOON TEA", "OBLIX EASY"],
      item1: true,
      item2: false,
      temp:'',
      value:''
    }
  },
  computed: {
    currentEastComponent() {
      return <menuItem value={this.menuEast.toLowerCase()} />
    }
  },
  methods: {
    changeMenuEast(tab) {
      this.menuEast = tab
      this.$emit('eastButtonChange', tab)
    },

    activeMenu(tab){
      this.temp = document.getElementById('btn')
      if(tab=== 'AFTERNOON TEA') {
        this.temp.style.opacity = 1;
      } else if(tab === 'OBLIX EASY') {
        this.temp.style.opacity = 1;
      }
      else {
        this.temp.style.opacity = 0.2;
      }

    },
    activeTAb(value) {
      value = this.menuEast
      this.temp = document.getElementById('btn')
      this.temp.style.opacity = (this.temp === 'AFTERNOON TEA') ? 1 : 0.2

      console.log(this.temp, value)
    }




    // changeOpacity() {
    //   this.typeButton = document.querySelector('.type-menu__button')
    //   this.typeButton.addEventListener('click', ()=>{
    //     if(this.typeButton === true)
    //     this.typeButton.style.opacity = 1
    //   })
    // }
  }
}
</script>
