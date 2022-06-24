<script setup>
import { ref, computed } from 'vue';

const props = defineProps({
  categories: Array,
  products: Array,
});

const emit = defineEmits(['addProductToCart', 'removeProductFormCart']);

const filteredProducts = computed(() => {
  if (selectedCategories.value.length) {
    return props.products.filter((product) =>
      selectedCategories.value.includes(product.category)
    );
  }
  return props.products;
});

const selectedCategories = ref([]);
</script>

<template>
  <div class="border p-2">
    <div class="mb-4">
      <span v-for="category in props.categories" class="mr-4">
        <input type="checkbox" :value="category" v-model="selectedCategories" />
        <label for="category">{{ category }}</label>
      </span>
    </div>
    <div class="flex">
      <div
        v-for="(product, index) in filteredProducts"
        :key="index"
        class="border-2 my-2 shadow-lg w-36 flex flex-col gap-2 p-2"
      >
        <div>Name: {{ product.name }}</div>
        <div>Price: {{ product.price }}</div>
        <div>Cat: {{ product.category }}</div>
        <button
          class="border p-2 bg-green-600 text-white"
          @click="emit('addProductToCart', product)"
          v-if="product.selectedQuantity === 0"
        >
          Add to cart
        </button>
        <div v-else>
          <button
            @click="emit('removeProductFormCart', product)"
            class="border p-2"
          >
            -
          </button>
          {{ product.selectedQuantity }}
          <button @click="emit('addProductToCart', product)" class="border p-2">
            +
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
