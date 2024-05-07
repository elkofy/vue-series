<script setup>
defineProps(["fileStructure"]);
const model = defineModel();
function addFileOrFolder(child) {
  if(model.value.includes(child)){
    model.value = model.value.filter((file) => file !== child);
    return;
  }
  model.value =[...model.value , child];
}
</script>

<template>
<ul>
  <li v-for="child in fileStructure.children" :key="child.name">
    <span>{{ child.name }}</span>
    <input type="checkbox" @change="addFileOrFolder(child.name)" >
    <Treeview v-if="child.type === 'folder'" :fileStructure="child" v-model="model" />
  </li>
</ul>
</template>
