<script setup>
import { ref } from 'vue';

const text = ref('John');
</script>

<template>
  <div>
    {{ text }}
  </div>
  Old way:
  <input
    class="mt-2"
    :value="text"
    @input="(event) => (text = event.target.value)"
  />
  <br />
  Vue way: <input class="mt-2" v-model="text" />
</template>
