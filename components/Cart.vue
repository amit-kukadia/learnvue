<script setup>
import { computed } from 'vue';

const props = defineProps({
  selectedProducts: Array,
});

const total = computed(() => {
  return props.selectedProducts.reduce((accumulator, product) => {
    return product.price * product.selectedQuantity + accumulator;
  }, 0);
});
</script>

<template>
  <div class="border p-2">
    <h4 class="font-bold mb-3">Cart</h4>
    <div class="mt-2">
      <div
        v-for="product in selectedProducts"
        class="flex justify-between my-1"
      >
        <div>{{ product.name }} * {{ product.selectedQuantity }}</div>
        <div>
          {{ product.selectedQuantity * product.price }}
        </div>
      </div>
    </div>
    <div class="font-bold mt-2">Total : {{ total }}</div>
  </div>
</template>
