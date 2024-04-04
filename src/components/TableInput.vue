<script setup>


</script>

<template>
  <div class="form">
    <label for="country">Country</label>
    <select id="country">
      <option>Option 1</option>
      <option>Option 2</option>
      <option>Option 3</option>
    </select>
    <label for="city">City</label>
    <select>
      <option>Option 1</option>
      <option>Option 2</option>
      <option>Option 3</option>
    </select>
    <label for="neighborhood">City</label>
    <select>
      <option>Option 1</option>
      <option>Option 2</option>
      <option>Option 3</option>
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
