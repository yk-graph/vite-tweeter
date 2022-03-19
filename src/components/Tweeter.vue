<script setup lang="ts">
import { ref } from 'vue'
defineProps<{ title: string }>()

const tweets = ref([
  {id: 1, item: 'はじめまして！'},
  {id: 2, item: 'こんばんは！'},
  {id: 3, item: 'おはようございます！'},
])
const inputItem = ref<string>('')

const createId = () => tweets.value.length + 1
const addItem = () => {
  tweets.value.push({ id: createId(), item: inputItem.value})
  inputItem.value = ''
}
const deleteItem = (id: number) => tweets.value = tweets.value.filter(tweet => tweet.id !== id)

</script>

<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <div class="input-container">
      <input type="text" v-model="inputItem">
      <button @click="addItem()">post</button>
    </div>
    <div class="list-container">
      <ul v-if="tweets.length !== 0">
        <li v-for="tweet in tweets" :key="tweet.id">
          {{ tweet.item }}
          <button @click="deleteItem(tweet.id)">削除</button>
        </li>
      </ul>
      <p v-else>現在投稿は0件です</p>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 540px;
  margin: 0 auto;
}
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
.list-container ul {
  width: 480px;
  padding: 0;
  margin: 0 auto;
}
.list-container ul li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px;
  margin-bottom: 1rem;
  background: lavender;
  list-style: none;
  text-align: left;
  border-radius: 4px;
}
.list-container ul li button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  background: darkcyan;
  color: white;
  cursor: pointer;
}
</style>
