<script setup>
import { ref } from "vue";
import { countryList, cityPerCountry, neighborhoodPerCity } from "../constants/countries";
let country = ref("");
let city = ref("");
let neighborhood = ref("");

</script>

<template>
  {{ country }}
  <div class="form">

    <label for="country">Country</label>
    <select id="country" v-model="country">
      <option v-for="country in countryList" :key="country">{{ country }}</option>
    </select>
    <label for="city" >City</label>
    <select v-model="city">
     <option v-for="city in cityPerCountry[country]" :key="city">{{ city }}</option>
    </select>
    <label for="neighborhood">City</label>
    <select v-model="neighborhood">
     <option v-for="neighborhood in neighborhoodPerCity[city]" :key="neighborhood">{{ neighborhood }}</option>
    </select>
  </div>

</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 1rem;
}
</style>
