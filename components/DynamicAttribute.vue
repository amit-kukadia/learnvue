<script setup>
import { ref } from 'vue';
const isDisabled = ref(false);
const name = ref('John');
const toggle = () => (isDisabled.value = !isDisabled.value);
</script>

<template>
  <p>{{ name }}</p>
  <input
    v-model="name"
    :disabled="isDisabled"
    class="w-24 mr-2 border-3 border-black"
  />
  <button @click="toggle">Toggle</button>
</template>
