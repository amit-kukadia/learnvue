<script setup>
import { ref } from 'vue';
import Child from './Child.vue';
const initialCount = 10;
const childCount = ref(initialCount);
const onChildCountChange = (newValue) => {
  childCount.value = newValue;
};
</script>

<template>
  <div>Child count in parent : {{ childCount }}</div>
  <Child
    class="mt-4"
    :initialCount="initialCount"
    :incrementBy="2"
    @onIncrement="onChildCountChange"
  />
</template>
