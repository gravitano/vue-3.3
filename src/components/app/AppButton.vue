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
  <button>
    <slot name="prefix" />
    <slot />
    <slot name="suffix" />
  </button>
</template>
