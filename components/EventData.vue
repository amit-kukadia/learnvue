<script setup>
const products = [
  {
    productName: 'Phone',
    cost: 100,
  },
  {
    productName: 'TV',
    cost: 50,
  },
];

const logProduct = (event, product) => console.log(event, product.productName);
</script>

<template>
  <div
    v-for="(product, index) in products"
    :key="product.productName"
    class="my-2 border w-full p-2"
    @click="logProduct($event, product)"
  >
    {{ index }}. Name is {{ product.productName }} and cost is
    {{ product.cost }}
  </div>
</template>
