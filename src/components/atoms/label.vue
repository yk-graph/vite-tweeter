<template>
  <label>
    {{ labelText }}
  </label>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
interface Props {
  labelText: string | number
}
defineProps<Props>()
</script>

<style scoped>
label {
  font-size: 1.2rem;
  color: #3d3d3d;
}
</style>
