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
  <div
    class="rounded-lg bg-white transition duration-300 shadow-sm hover:shadow-lg px-4 py-4 flex flex-col gap-4"
  >
    <img
      :src="product.image"
      :alt="product.title"
      class="w-full h-[240px] object-cover"
    />
    <h3 class="text-lg font-semibold">{{ product.title }}</h3>
    <div class="flex-1">
      <article class="text-sm text-gray-700 line-clamp-4">
        {{ product.description }}
      </article>
      <div class="flex justify-between text-sm text-gray-500 mt-3">
        <p>Price: {{ localePrice }}</p>
        <p>Rating: {{ formattedRate }}</p>
      </div>
    </div>
    <AppButton @click="emit('buy')">Buy Now</AppButton>
  </div>
</template>
