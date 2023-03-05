<script setup>
import NavMenu from '@/components/NavMenu.vue'
</script>

<template>
  <h1>Call API</h1>
  <div class="card-divider">
    <p>{{ joke }}</p>
    <p>{{ url }}</p>
    <p>{{ date }}</p>
    <p>{{ id }}</p>
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
}
</script>

<style>
.item {
}
.item li {
  display: inline-block;
  border: 1px solid;
  width: 180px;
  text-align: center;
  padding: 5px;
}
</style>
