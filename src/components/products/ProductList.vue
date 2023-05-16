<script setup lang="ts" generic="T extends Product">
import type { Product } from './types';

defineProps<{
  products: T[];
}>();
</script>

<template>
  <div>
    <h1>Products</h1>
    <ul>
      <li v-for="product in products" :key="product.id">
        {{ product.title }}
      </li>
    </ul>
  </div>
</template>
