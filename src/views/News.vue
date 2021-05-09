<template>
  <h1 class="text-center text-4xl text-white font-bold m-4">Crypto News</h1>
  <div class="container grid gap-1 mx-auto my-2 min-h-screen text-center lg:grid-cols-2">
    <div class="flex rounded-lg p-2 m-6 shadow-2xl" v-for="item in news" :key="item">
      <div class="flex bg-blueGray-500 bg-opacity-50 text-white rounded-lg">
        <img class="h-40 w-40 pt-4 pl-4" :src="`${item.imageurl}`" alt="Image URL" />
        <div class="m-4 text-center">
          <div>
            <a
              class="text-2xl font-bold hover:underline hover:text-white"
              v-bind:href="item.guid"
              target="_blank"
              rel="noopener noreferrer"
            >{{ item.title }}</a>
          </div>
          <div>
            <p class="text-base m-2">{{ item.body }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'news',
  data: () => ({
    news: [],
    errors: []
  }),
  created() {
    axios.get('https://min-api.cryptocompare.com/data/v2/news/?lang=EN')
      .then(response => {
        this.news = response.data.Data
        console.log(response.data.Message)
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
}
</script>
