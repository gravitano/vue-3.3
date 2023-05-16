<script setup lang="ts">
import type { ButtonProps } from './types';

defineProps<ButtonProps>();
</script>

<template>
  <button>
    <slot />
  </button>
</template>
