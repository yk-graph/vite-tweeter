<template>
  <Label label-text="aaaaaaaaa" />
  <Input v-model="text" />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Label from '../atoms/Label.vue'
import Input from '../atoms/Input.vue'

const text = ref('')
</script>

<style scoped></style>
