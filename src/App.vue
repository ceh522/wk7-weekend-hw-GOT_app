<template>
    <div id="app">
      <nav>
      <h1>Game of Thrones</h1>
    </nav>
    <house-list :houses="houses" />
    <house-detail />
    </div>
</template>

<script>

import HouseList from './components/HouseList.vue'
import HouseDetail from './components/HouseDetail.vue'


export default {
  name: 'app',
  data(){
    return {
      houses: []
    }
  },
  components: {
    "house-list": HouseList,
    "house-detail": HouseDetail,
  },

  mounted(){
    fetch('https://anapioficeandfire.com/api/houses/')
    .then(data => data.json())
    .then(houses=> this.houses= houses)
  }
}
</script>

<style lang="css" scoped>

#app {
  background-image: url("./assets/ice_and_fire.jpg");
  background-size:cover, 50px;
  background-repeat: no-repeat;
}

h1 {
  text-align: center;
  font-size: 35px;
  color: #333;
}

nav {
  box-sizing: border-box;
  background-color: white;
  overflow: auto;
  position: relative;
  top: 0;
  width: 100%;
  text-align: center;
  font-weight: 100;
  letter-spacing: 2px;
  padding: 20px;
}

</style>
