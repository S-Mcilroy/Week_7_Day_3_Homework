<template lang="html">
  <div>
    <input type="text" name="" value="" v-model="searchCountry" v-on:ValueChange="searchBar">
    <select v-on:change="handleChange" v-model="selectedCountry">
      <option value="" disabled selected>Select a Country</option>
      <option v-for="(country, index) in countries" :value="country" :key="index">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from "../main.js"

export default {
  name: 'countries-list',
  data(){
    return{
      selectedCountry: [],
      searchCountry: ""
    }
  },
  props: ["countries"],
    methods: {
      handleChange(){
        eventBus.$emit('country-selected', this.selectedCountry)
      },
      searchBar(){
        
      }
    }
}
</script>

<style lang="css" scoped>
</style>
