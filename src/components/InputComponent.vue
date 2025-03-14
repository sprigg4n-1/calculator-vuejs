<script setup lang="ts">
const props = defineProps({
  value: String,
})
</script>

<template>
  <input v-model="props.value" class="calculator__screen-bottom" placeholder="0" />
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
