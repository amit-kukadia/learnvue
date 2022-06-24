<script setup>
import { ref, watch } from 'vue';

const x = ref(0);

watch(x, (newX, oldX) => {
  console.log(`new x is ${newX}, old x is ${oldX}`);
  if (newX % 3 === 0) {
    alert(`${newX} is a multiple of 3`);
  }
});
</script>

<template>
  <button @click="x++">x is: {{ x }}</button>
</template>
