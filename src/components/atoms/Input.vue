<template>
  <input v-model="inputValue">
</template>

<script setup lang="ts">
import { defineProps, defineEmits, computed } from 'vue'
interface Props {
  modelValue: string
}
const props = defineProps<Props>()

interface Emits {
  (e: 'update:modelValue', value: string): void
}
const emit = defineEmits<Emits>()

const inputValue = computed({
  get: () => props.modelValue,
  set: (value) => {
    // 値に変更があると呼ばれるsetter
    emit('update:modelValue', value)
  },
})
</script>

<style scoped></style>
