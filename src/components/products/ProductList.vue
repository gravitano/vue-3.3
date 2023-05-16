<script setup lang="ts" generic="T extends Product">
import ProductItem from './ProductItem.vue';
import type { Product } from './types';

defineProps<{
  products: T[];
}>();
</script>

<template>
  <div class="mt-4">
    <h1 class="text-2xl font-semibold mb-3">Products</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 lg:gap-8">
      <ProductItem
        v-for="product in products"
        :key="product.id"
        :product="product"
        @buy="console.log('buy', product)"
      />
    </div>
  </div>
</template>
