<script setup>
import { ref } from 'vue';
const props = defineProps({
  initialCount: Number,
  incrementBy: Number,
});

const emit = defineEmits(['onIncrement']);

const count = ref(props.initialCount);

const increment = () => {
  count.value += props.incrementBy;
  emit('onIncrement', count.value);
};
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
