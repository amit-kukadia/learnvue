<script setup>
import { ref, reactive } from 'vue';

const count = ref(0);

const state = reactive({ count: 0 });
</script>

<template>
  <button @click="count++">Ref Count is: {{ count }}</button>
  <br />

  <button @click="state.count++">Reactive Count is: {{ state.count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
