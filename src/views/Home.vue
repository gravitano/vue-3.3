<script setup lang="ts">
import AppInput from '@/components/app/AppInput.vue';
import ProductList from '@/components/products/ProductList.vue';
import type { Product } from '@/components/products/types';
import { ref, watch } from 'vue';
import { watchDebounced } from '@vueuse/core';

const search = ref('');
const products = ref<Product[]>([]);

function fetchData() {
  fetch(`https://fakestoreapi.com/products?search=${search.value}`)
    .then((res) => res.json())
    .then((data) => {
      products.value = data as Product[];
    });
}

fetchData();

watch(search, () => {
  fetchData();
});

watchDebounced(
  search,
  () => {
    fetchData();
  },
  { debounce: 500, maxWait: 3000 }
);
</script>

<template>
  <h1 class="text-4xl font-semibold mb-4">Welcome Vue 3.3!</h1>
  <AppInput v-model="search" placeholder="Search" />
  <ProductList :products="products" />
</template>
