<template>
    <div class="container mx-auto">
        <div class="flex bg-gray-400 rounded-lg p-2 m-6 shadow-2xl" v-for="item in news">
            <div class="">
                <a class="card-title text-2xl hover:underline hover:text-blueGray-600" v-bind:href="item.guid">{{item.title}}</a>
                <img class="flex-auto h-24 w-24 m-2" v-bind:src="item.imageurl" alt="">
                <div class="">
                    <h1 class="flex-auto">
                        {{item.body}}
                    </h1>
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
  created () {
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