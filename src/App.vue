<template lang="html">
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <countries-list :countries='countries'></countries-list>
      <country-detail :country ='selectedCountry'></country-detail>
      </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return{
      countries: [],
      selectedCountry: null
    };
  }, mounted(){
      fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(countries => this.countries = countries)

      eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }
}
</script>

<style lang="css" scoped>
</style>

<!-- <input id="searchbar" onkeyup="search_country()" type="text"
name="search" placeholder="Search Countries..">  -->

<!-- function search_country() {
    let input = document.getElementById('searchbar').value
    input=input.toLowerCase();
    let countriesList = this.countries;

    for (i = 0; i < countriesList.length; i++) {
        if (!countriesList[i].innerHTML.toLowerCase().includes(input)) {
            countriesList[i].style.display="none";
        }
        else {
            countriesList[i].style.display="list-item";
        }
    }
}  -->
