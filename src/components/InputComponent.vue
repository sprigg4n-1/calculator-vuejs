<script setup lang="ts">
const modelValue = defineModel<string>()
</script>

<template>
  <input v-model="modelValue" class="calculator__screen-bottom" placeholder="0" />
</template>

<style scoped>
.calculator__screen-bottom {
  font-size: 24px;
  font-weight: bold;
  background-color: transparent;
  border: none;
  text-align: right;
  color: white;
  padding: 5px 10px;
  width: 100%;
  background-color: rgb(0, 0, 0);
}
</style>
