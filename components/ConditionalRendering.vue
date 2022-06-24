<script setup>
import { ref } from 'vue';

const display = ref(false);
const toggle = () => (display.value = !display.value);
</script>

<template>
  <button @click="toggle" class="border">Toggle</button>
  <button @click="display = 'something else'" class="ml-4 border">
    Make it something else
  </button>

  <div v-if="display === true">display is true</div>
  <div v-else-if="display === false">display is false</div>
  <div v-else>display is something else</div>

  <div v-show="display">v-display is true</div>
</template>
