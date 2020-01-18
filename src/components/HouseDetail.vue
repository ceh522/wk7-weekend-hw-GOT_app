<template lang='html'>
  <div v-if="house" id="houseDetail">
    <div id="detailWrapper">
      <h2>{{house.name}}</h2>
      <div id="flexwrapper">
        <div  id="left">
          <p><span>Region</span>: {{house.region}}</p>
          <p><span>Coat of Arms</span>: {{house.coatOfArms}}</p>
          <p><span>Words</span>: {{house.words}}</p>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import { eventBus } from '../main.js'

export default {
  name: 'house-detail',
  data(){
    return {
      house: null,
    }
  },
  mounted(){
    eventBus.$on('house-selected', (house) => {
      this.house = house
    })
  }
}
</script>

<style lang="css" scoped>

#detailWrapper {
  box-sizing: border-box;
  background: white;
  padding: 10px;
  height: 100%;
  border-radius: 3px;
}
#flexWrapper {
  display: flex;
  justify-content: space-between;
}
#left p:first-child {
    margin-top: 0;
  }
h2 {
  margin: 10px 0 20px;
  padding: 0;
}
p span {
  font-weight: bold;
}
</style>
