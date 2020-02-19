<template lang="html">
  <section v-if="country">
    <h3>Name: {{country.name}}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p>Languages:</p>
    <ul>
      <li v-for="(language, index) in country.languages" :value="language" :key="index">{{language.name}}</li>
    </ul>

    <img :src="country.flag" height="200" width="300"/>
  </section>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
