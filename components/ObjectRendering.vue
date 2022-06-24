<script setup>
const productDetail = {
  brand: 'Samsung',
  category: 'Televison',
  cost: 200,
  rating: 4,
};
</script>

<template>
  <div
    v-for="(value, key, index) in productDetail"
    :key="index"
    class="my-2 border w-full p-2"
  >
    {{ index + 1 }}. {{ key }} is {{ value }}
  </div>
</template>
