<script setup>
import { ref } from 'vue';
const name = ref('Amit');
const profession = 'Software developer';
const age = ref(20);
age.value++;
const increment = () => age.value++;
</script>

<template>
  <p>{{ name }} - {{ profession }} - {{ age }}</p>
  <br />
  <input v-model="name" class="w-24 mr-2 border-3 border-black" />
  <button @click="increment">Increment age</button>
</template>
