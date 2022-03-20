<script setup lang="ts">
  import { ref, defineEmits } from 'vue';
  const emit = defineEmits(['add-item']);

  const inputItem = ref<string>('');

  const addItem = () => {
    emit('add-item', inputItem.value)
    inputItem.value = ''
  };
</script>

<template>
  <div class="input-container">
    <input type="text" v-model="inputItem">
    <button @click="addItem()">post</button>
  </div>
</template>

<style scoped>
.input-container {
  background: darkkhaki;
  height: 8rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 2rem;
}
.input-container input {
  width: 240px;
  padding: 8px 16px;
  margin-bottom: 1rem;
  border: none;
  border-radius: 2px;
}
.input-container button {
  width: 160px;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background: darkcyan;
  color: white;
  cursor: pointer;
}
</style>
