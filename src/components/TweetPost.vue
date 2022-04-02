<template>
  <div class="form-container">
    <input
      v-model="inputText"
    >
    <button
      class="save-button"
      @click="addItem()"
    >
      post
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue'
const emit = defineEmits(['add-item'])

const inputText = ref<string>('')
const addItem = () => emit('add-item', inputText.value)
</script>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: aliceblue;
  padding: 24px 0;
  width: 600px;
  margin-bottom: 12px;
  border-radius: 4px;
}
.save-button {
  color: #fff;
  font-weight: bold;
  background-color: #68c9c9;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}
.save-button:hover {
  background-color: #37bdbd;
}
input {
  margin-bottom: 16px;
}
</style>