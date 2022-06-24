<script setup>
import { ref, computed } from 'vue';
const count1 = ref(5);
const count2 = ref(5);
const sum = computed(() => {
  return count1.value + count2.value;
});
</script>

<template>
  <div class="flex flex-col gap-2">
    <div @click="count1++">Increment count1: {{ count1 }}</div>
    <div @click="count2++">Increment count2: {{ count2 }}</div>
    <div>Sum is {{ sum }}</div>
  </div>
</template>
