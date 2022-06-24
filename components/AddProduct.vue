<script setup>
import { ref } from 'vue';

const props = defineProps({
  categories: Array,
});

const emit = defineEmits(['addProduct']);

const name = ref('');
const price = ref();
const category = ref('Electronics');

const addProduct = (name, price, category) => {
  emit('addProduct', { name, price, category, selectedQuantity: 0 });
};
</script>

<template>
  <div class="border p-2">
    <h4 class="font-bold mb-3">Add product</h4>

    <form
      @submit.prevent="addProduct(name, price, category)"
      class="flex flex-col gap-4"
    >
      <input type="text" v-model="name" placeholder="Name" />
      <input type="number" v-model="price" placeholder="Price" />
      <select v-model.number="category">
        <option v-for="category in props.categories" :value="category">
          {{ category }}
        </option>
      </select>
      <button>Add Product</button>
    </form>
  </div>
</template>
