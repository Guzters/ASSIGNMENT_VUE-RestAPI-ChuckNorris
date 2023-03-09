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
  <main>
    <h1 class="header">Chuck Norris Joke Generator</h1>
    <div class="button">
      <button @click="getRandomJoke">Generate New Joke</button>
    </div>
    <div class="joke_info">
      <p>JOKE : {{ joke }}</p>
      <p>URL : {{ url }}</p>
      <p>DATE : {{ date }}</p>
      <p>ID : {{ id }}</p>
    </div>
  </main>
</template>

<style lang="postcss" scoped>
main {
  @apply bg-gradient-to-t from-red-500 via-purple-400 to-blue-700;
  height: 900px;
  & .header {
    @apply items-center justify-center rounded-lg bg-slate-400 text-center text-2xl;
  }

  & .button {
    @apply w-1/5 rounded-sm border-4 border-black bg-blue-900 px-4 py-2 text-center text-white hover:bg-blue-700;
    margin-top: 1%;
    margin-bottom: 1%;
    margin-left: 40%;
  }
  & .joke_info {
    @apply inline-block w-6/12 rounded-lg border-4 border-black bg-yellow-200 py-5 text-center;
    margin-left: 25%;
  }
}
</style>
