<script setup>
import Treeview from "./components/Treeview.vue";
import {ref} from "vue";
const fileStructure = {
  name: "src",
  type: "folder",
  children: [
    {
      name: "components",
      type: "folder",
      children: [
        {
          name: "TreeItem.vue",
          type: "file",
        },
        {
          name: "Treeview.vue",
          type: "file",
        },
      ],
    },
    {
      name: "App.vue",
      type: "file",
    },
  ],
};
const selectedFiles = ref([]);
</script>

<template>
  <h1>Vue Series</h1>
  {{ selectedFiles }}
  <Treeview :file-structure="fileStructure"  v-model="selectedFiles"/>
</template>

<style scoped>

</style>
