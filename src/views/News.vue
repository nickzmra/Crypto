<template>
  <h1 class="text-center text-4xl text-white font-bold m-4">Crypto News</h1>
  <div class="container grid gap-1 mx-auto my-2 text-center lg:grid-cols-2">
    <div class="flex rounded-lg p-2 m-6 shadow-2xl" v-for="item in news">
      <div class="flex bg-blueGray-500 rounded-lg">
        <img class="h-40 w-40 pt-4 pl-4" :src="`${item.imageurl}`" alt="Image URL" />
        <div class="m-4 text-center">
          <a
            class="text-2xl font-bold hover:underline hover:text-white"
            v-bind:href="item.guid"
          >{{ item.title }}</a>
          <p class="text-base m-2">{{ item.body }}</p>
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
        console.log(response.data.Message) // This will give you access to the full object
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
}
</script>
<!--
<template>
  <div class="flex max-w">
    <div class="flex bg-gray-400 rounded-lg p-2 m-6 shadow-2xl" v-for="item in news">
      <div class="flex">
        <a
          class="card-title text-2xl hover:underline hover:text-blueGray-600"
          v-bind:href="item.guid"
        >{{ item.title }}</a>
        <img class="flex-auto h-24 w-24 m-2" v-bind:src="item.imageurl" :alt="``" />
        <img class="h-24 w-24 m-4" :src="`${item.imageurl}`" alt="Image URL" />
        <div class>
          <h1 class="flex-auto">{{ item.body }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>
-->