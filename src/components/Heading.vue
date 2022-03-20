<script setup lang="ts">
  import { defineProps } from 'vue';
  type Props = {
    title: string
  };
  defineProps<Props>();
</script>

<template>
  <h1>{{ title }}</h1>
</template>

<style scoped>
h1 {
  text-align: center;
}
</style>
