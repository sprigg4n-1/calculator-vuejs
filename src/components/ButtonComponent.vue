<script setup lang="ts">
const props = defineProps({
  value: String,
  isBig: Boolean,
})
</script>

<template>
  <button class="calculator__buttons-btn" :class="{ 'btn-2': isBig }">
    {{ props.value }}
  </button>
</template>

<style scoped>
.calculator__buttons-btn {
  width: 25%;
  border: none;
  height: 70px;
  font-size: 24px;
  border: 1px solid rgb(39, 39, 39);
  cursor: pointer;
  background-color: rgb(168, 168, 168);
}

.calculator__buttons-btn:hover {
  background-color: white;
  transition: 0.3s all;
}

.calculator__buttons-btn.btn-2 {
  width: 50%;
}
</style>
