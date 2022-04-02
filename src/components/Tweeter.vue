<template>
  <div class="container">
    <h1>Tweeter</h1>
    <TweetPost @add-item="addItem" />
    <div class="tweet-container">
      <p v-if="itemLists.length === 0">
        No tweets have been added
      </p>
      <ul v-else>
        <TweetList
          :item-lists="itemLists"
          @delete-item="deleteItem"
        />
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import TweetPost from './TweetPost.vue'
import TweetList from './TweetList.vue'

type ItemLists = {
  id: number,
  text: string
}

const itemLists = ref<ItemLists[]>([
  {id: 1, text: 'React'},
  {id: 2, text: 'Vue'},
  {id: 3, text: 'JavaScript'},
])

const addItem = (text: string) => itemLists.value.push({ id: Math.random(), text })
const deleteItem = (id: number) => itemLists.value = itemLists.value.filter(list => list.id !== id)
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>