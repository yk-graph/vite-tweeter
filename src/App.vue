<script setup lang="ts">
  import { ref } from 'vue';
  import Heading from './components/Heading.vue';
  import InputBox from './components/InputBox.vue';
  import TweetLists from './components/TweetLists.vue';

  const tweets = ref([
    {id: 1, item: 'はじめまして！'},
    {id: 2, item: 'こんばんは！'},
    {id: 3, item: 'おはようございます！'},
  ]);

  const createId = () => tweets.value.length + 1
  const addItem = (item: string) => tweets.value.push({ id: createId(), item})
  const deleteItem = (id: number) => tweets.value = tweets.value.filter(tweet => tweet.id !== id)
</script>

<template>
  <div class="container">
    <Heading title="Tweeter" />
    <InputBox @add-item="addItem" />
    <TweetLists :tweets="tweets" @delete-item="deleteItem" />
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  width: 540px;
  margin: 0 auto;
}
</style>
