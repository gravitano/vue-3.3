<script setup lang="ts">
import AppButton from '@/components/app/AppButton.vue';
import ProductList from '@/components/products/ProductList.vue';
import type { Product } from '@/components/products/types';
import { ref } from 'vue';

const products = ref<Product[]>([]);

fetch('https://fakestoreapi.com/products')
  .then((res) => res.json())
  .then((data) => {
    products.value = data as Product[];
  });
</script>

<template>
  <h1>Welcome</h1>
  <ProductList :products="products" />
  <AppButton>Click me</AppButton>
</template>
