<script setup lang="ts">
const modelValue = defineModel<string>();
</script>

<template>
  <input type="text" v-model="modelValue" />
</template>
