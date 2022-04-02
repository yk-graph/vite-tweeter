<template>
  <button
    :class="typeColor"
    :disabled="disabled"
  >
    {{ buttonText }}
  </button>
</template>

<script setup lang="ts">
import { defineProps, computed } from 'vue'
interface Props {
  buttonText: string | number
  type: 'primary' | 'secondary'
  disabled?: boolean
}
const props = defineProps<Props>()

const typeColor = computed(() =>
  props.type === 'primary' ? 'primary' : 'secondary'
)
</script>

<style scoped>
button {
  padding: 8px 32px;
  font-size: 1.2rem;
  border: none;
  border-radius: 2px;
  cursor: pointer;
  transition: all 0.2s;
}
button:hover {
  opacity: 0.8;
}
button:disabled {
  background: #636363;
  color: #3d3d3d;
}
.primary {
  background: #9d9d2d;
  color: #ffffff;
}
.secondary {
  background: #d1d1c9;
  color: #454444;
}
</style>
