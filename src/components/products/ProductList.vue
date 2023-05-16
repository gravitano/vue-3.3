<script setup lang="ts" generic="T extends Product">
import ProductItem from './ProductItem.vue';
import type { Product } from './types';

defineProps<{
  products: T[];
}>();
</script>

<template>
  <div>
    <h1>Products</h1>
    <ul>
      <ProductItem
        v-for="product in products"
        :key="product.id"
        :product="product"
      />
    </ul>
  </div>
</template>
