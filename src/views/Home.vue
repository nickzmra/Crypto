<template>
  <div class="container mx-auto min-h-screen">
    <h1
      class="text-4xl text-center mt-6 mb-10 tracking-wider font-thick font-bold text-white"
    >Total Coin List</h1>
    <div class="container grid lg:grid-cols-2">
      <div>
        <div
          class="grid grid-cols-2 grid-rows-1 text-white text-xl bg-emerald-600 rounded-md p-4 m-2 mb-4"
        >
          <div>Name</div>
          <div>Description</div>
        </div>
      </div>
      <div
        class="grid grid-cols-2 grid-rows-1 text-white text-xl bg-emerald-600 rounded-md p-4 m-2 mb-4"
      >
        <div>Name</div>
        <div>Description</div>
      </div>
      <div v-for="thing in list" :key="thing">
        <div
          class="grid grid-cols-2 text-white bg-blueGray-500 bg-opacity-50 p-2 m-2 text-justify rounded-md hover:border-pink-500"
        >
          <div>
            <a
              class="text-2xl font-bold hover:underline hover:text-white"
              v-bind:href="'https://cryptocompare.com' + thing.Url"
              target="_blank"
              rel="noopener noreferrer"
            >
              {{ thing.FullName }}
              <img
                class="mt-4 ml-1 h-20 w-20"
                v-bind:src="'https://cryptocompare.com' + thing.ImageUrl"
              />
            </a>
          </div>
          <div
            class="overflow-auto h-36 bg-blueGray-300 text-black p-2 rounded-sm"
          >{{ thing.Description }}</div>
        </div>
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