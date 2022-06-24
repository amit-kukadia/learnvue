<script setup>
import { ref, computed } from 'vue';
import AddProduct from './AddProduct.vue';
import ProductList from './ProductList.vue';
import Cart from './Cart.vue';
const categories = ['Electronics', 'Clothing'];
const products = ref([
  {
    name: 'TV',
    price: 100,
    category: 'Electronics',
    selectedQuantity: 0,
  },
  {
    name: 'Shirt',
    price: 15,
    category: 'Clothing',
    selectedQuantity: 0,
  },
]);

const selectedProducts = computed(() => {
  return products.value.filter((product) => product.selectedQuantity > 0);
});

const addProduct = (product) => {
  products.value.push(product);
};

const addProductToCart = (product) => {
  const productIndex = products.value.findIndex(
    (el) => el.name === product.name
  );
  products.value[productIndex].selectedQuantity++;
};

const removeProductFormCart = (product) => {
  const productIndex = products.value.findIndex(
    (el) => el.name === product.name
  );
  products.value[productIndex].selectedQuantity--;
};
</script>

<template>
  <div class="flex">
    <div class="w-48">
      <AddProduct :categories="categories" @addProduct="addProduct" />
      <Cart :selectedProducts="selectedProducts" />
    </div>
    <ProductList
      :categories="categories"
      :products="products"
      @addProductToCart="addProductToCart"
      @removeProductFormCart="removeProductFormCart"
    />
  </div>
</template>
