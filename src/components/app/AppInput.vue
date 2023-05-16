<script setup lang="ts">
const modelValue = defineModel<string>();
</script>

<template>
  <input
    type="text"
    class="rounded-lg w-full border-gray-300 focus:border-amber-500 focus:ring-amber-500"
    v-model="modelValue"
  />
</template>
