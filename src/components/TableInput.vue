<script setup lang="ts">
import { ref } from "vue";
const model = defineModel({ type: String })

import { countryList, cityPerCountry, neighborhoodPerCity } from "../constants/countries";
let country = ref("");
let city = ref("");
let neighborhood = ref("");
 
const resetUnselected = ( types : string[]) => {
  for (let type of types) {
    switch(type) {
      case "country":
        city.value = "";
        neighborhood.value = "";
        break;
      case "city":
        neighborhood.value = "";
        break;
    }
  }
}
const updateValue = (e, type ) => {
  switch(type) {
    case "country":
      country.value = e.target.value;
      resetUnselected(["city","neighborhood"]);
      break;
    case "city":
      city.value = e.target.value;
      resetUnselected(["neighborhood"]);
      break;
    case "neighborhood":
      neighborhood.value = e.target.value;
      break;
  }
  model.value = e.target.value;
}
</script>

<template>
  <div class="form">
    <label for="country">Country</label>
    <select v-model="country" id="country" @input="updateValue($event,'country')">
      <option v-for="country in countryList" :key="country">{{ country }}</option>
    </select>
    <template v-if="country">
      <label for="city" >City</label>   
    <select  v-model="city" value="" @input="updateValue($event,'city')">
     <option v-for="city in cityPerCountry[country]" :key="city">{{ city }}</option>
    </select>
    </template>
    <template v-if="city">

    <label for="neighborhood">Neighborhood</label>
    <select v-if="city" v-model="neighborhood" value="" @input="updateValue($event,'neighborhood')">
    <option v-for="neighborhood in neighborhoodPerCity[city]" :key="neighborhood">{{ neighborhood }}</option>
    </select>
  </template>

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
