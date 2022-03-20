<script setup lang="ts">
  import { defineProps, defineEmits } from 'vue';
  type Tweet = {
    id: number;
    item: string;
  };
  type Props = {
    tweets: Tweet[]
  };
  defineProps<Props>();
  const emit = defineEmits(['delete-item'])

  const deleteItem = (id: number) => emit('delete-item', id)
</script>

<template>
  <div class="list-container">
    <ul v-if="tweets.length !== 0">
      <li v-for="tweet in tweets" :key="tweet.id">
        {{ tweet.item }}
        <button @click="deleteItem(tweet.id)">削除</button>
      </li>
    </ul>
    <p v-else>現在投稿は0件です</p>
  </div>
</template>

<style scoped>
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
