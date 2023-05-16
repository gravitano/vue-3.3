<script setup lang="ts">
import { computed } from 'vue';
import type { Product } from './types';
import AppButton from '../app/AppButton.vue';

const { product } = defineProps<{
  product: Product;
}>();

const emit = defineEmits<{
  buy: [];
}>();

const formattedRate = computed(() => {
  return product.rating.rate.toFixed(2);
});

const localePrice = computed(() => {
  return new Intl.NumberFormat('en-US', {
    style: 'currency',
    currency: 'USD',
  }).format(product.price);
});
</script>

<template>
  <div>
    <h1>{{ product.title }}</h1>
    <article>
      {{ product.description }}
    </article>
    <p>Price: {{ localePrice }}</p>
    <p>Rating: {{ formattedRate }}</p>
    <AppButton @click="emit('buy')">Buy Now</AppButton>
  </div>
</template>
