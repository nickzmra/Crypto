<template>
  <div class="container mx-auto min-h-screen">
    <h1
      class="text-4xl text-center mt-6 mb-10 tracking-wider font-thick font-bold text-white"
    >Total Coin List</h1>
    <div class="grid grid-cols-3 text-white bg-coolGray-500 rounded-md p-4 m-2">
      <div>Symbol</div>
      <div>Name</div>
      <div>Description</div>
    </div>
    <div v-for="thing in list" :key="thing">
      <div
        class="grid grid-cols-3 text-white bg-emerald-500 bg-opacity-50 p-4 m-3 rounded-md hover:border-pink-500"
      >
        <div>{{ thing.Symbol }}</div>
        <div>{{ thing.CoinName }}</div>
        <div class>{{ thing.Description }}</div>
      </div>
    </div>
  </div>
</template>

<script>
//import { user } from '../helpers/useAuth'
import axios from 'axios'
export default {
  name: 'list',
  data: () => ({
    list: [],
    errors: []
  }),
  created() {
    axios.get('https://min-api.cryptocompare.com/data/all/coinlist')
      .then(response => {
        this.list = response.data.Data
        console.log(response.data.Message)
      })
      .catch(e => {
        this.errors.push(e)
      })
  }
}
</script>