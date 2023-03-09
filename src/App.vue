<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const id = ref()
const url = ref()
const date = ref()
const joke = ref()

const getRandomJoke = async () => {
  const result = await axios.get('https://api.chucknorris.io/jokes/random')
  console.warn(result.data)
  id.value = result.data.id
  url.value = result.data.url
  date.value = result.data.created_at
  joke.value = result.data.value
}

onMounted(() => {
  getRandomJoke()
})
</script>

<template>
  <h1 class="header">Chuck Norris Joke Generator</h1>
  <div>
    <button class="rounded-sm bg-blue-500 px-4 py-2 hover:bg-blue-700" @click="getRandomJoke">Generate New Joke</button>
  </div>
  <div class="joke_info">
    <p>JOKE : {{ joke }}</p>
    <p>URL : {{ url }}</p>
    <p>DATE : {{ date }}</p>
    <p>ID : {{ id }}</p>
  </div>
</template>

<style>
.header {
  display: ;
}
.joke_info {
  display: inline-block;
  border: 1px solid;
  width: 1000px;
  text-align: center;
  padding: 5px;
  background-color: burlywood;
}
</style>
