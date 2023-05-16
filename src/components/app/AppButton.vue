<script setup lang="ts">
import type { ButtonProps } from './types';

defineProps<ButtonProps>();

defineSlots<{
  default?: (props: ButtonProps) => any;
  prefix?: (props: ButtonProps) => any;
  suffix?: (props: ButtonProps) => any;
}>();
</script>

<template>
  <button
    class="text-sm font-semibold bg-amber-500 hover:bg-amber-600 transition duration-300 text-white rounded-lg px-3 py-2"
  >
    <slot name="prefix" />
    <slot />
    <slot name="suffix" />
  </button>
</template>
