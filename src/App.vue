<script setup>
import TableInput from "./components/TableInput.vue";
import { ref } from "vue";

const myModel = ref("");
</script>

<template>
  <h1>Vue Series</h1>
  Your selection : {{ myModel }}
  <TableInput v-model="myModel"/>
</template>

<style scoped>

</style>
