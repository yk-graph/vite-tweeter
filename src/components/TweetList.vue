<template>
  <li
    v-for="list in itemLists"
    :key="list.id"
    class="tweet-list"
  >
    <span>{{ list.text }}</span>
    <button
      class="delete-button"
      @click="deleteItem(list.id)"
    >
      delete
    </button>
  </li>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'

type ItemLists = {
  id: number,
  text: string
}
interface Props {
  itemLists: ItemLists[]
}

const emit = defineEmits(['delete-item'])
const deleteItem = (id: number) => emit('delete-item', id)

defineProps<Props>()
</script>

<style scoped>
.tweet-list {
  list-style: none;
  margin-bottom: 12px;
  border-radius: 4px;
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  background-color: rgb(204, 219, 233);
  padding: 8px 20px;
  width: 300px;
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
.delete-button {
  color: #fff;
  font-weight: bold;
  background-color: #c99a68;
  border-radius: 2px;
  border: none;
  width: 60px;
  height: 22px;
}
.delete-button:hover {
  background-color: #ac783f;
}
input {
  margin-bottom: 16px;
}
label {
  font-size: 20px;
  font-weight: bold;
}
</style>