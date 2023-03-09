<script setup>
import NavMenu from '@/components/NavMenu.vue'
</script>

<template>
  <h1 class="header">Chuck Norris Joke Generator</h1>
  <div>
    <button id="clickMe">Generate New Joke</button>
  </div>
  <div class="joke_info">
    <p>JOKE : {{ joke }}</p>
    <p>URL : {{ url }}</p>
    <p>DATE : {{ date }}</p>
    <p>ID : {{ id }}</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return {
      id: null,
      url: null,
      date: null,
      joke: null,
    }
  },

  async mounted() {
    let result = await axios.get('https://api.chucknorris.io/jokes/random')
    console.warn(result.data)
    this.id = result.data.id
    this.url = result.data.url
    this.date = result.data.created_at
    this.joke = result.data.value
  },

  methods: {
    showAlert: (message) => {
      alert(message)
    },
  },
}
</script>

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
