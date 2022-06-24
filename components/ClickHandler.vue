<script setup>
import { ref } from 'vue';
const onClick = () => {
  alert('function call clicked');
};

const count = ref(0);
</script>

<template>
  <div v-on:mouseover="count++">Mouse over count: {{ count }}</div>
  <div class="mt-4" @click="onClick">function call clicked</div>
</template>
