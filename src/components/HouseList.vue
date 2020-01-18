<template lang="html">
  <select v-on:change="handleSelect" v-model="selectedHouse">
    <option disabled value="">Select a house...</option>
    <option v-for="house in houses" :value="house">{{house.name}}</option>
  </select>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'house-list',
  data(){
    return {
      "selectedHouse": {},
    }
  },
  props: ["houses"],
  methods: {
    handleSelect(){
      this.search = ""
      eventBus.$emit('house-selected', this.selectedHouse)
    }
  }
}
</script>

<style lang="css" scoped>
  form{
    text-align: center;
    margin: 40px 0;
  }
  select, input[type="text"]{
      font-size: 25px;
    }
    select {
      margin-left: 20px;
    }
    </style>
