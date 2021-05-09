<template>
    <h1 class="text-4xl text-center text-white font-bold m-6 pb-4">My Favorite Coins</h1>
    <div class="container gap-2 mx-auto my-2 min-h-screen">
        <div class="text-white">
            <div class="grid grid-cols-5 grid-rows-1 p-5 m-2 bg-coolGray-700 rounded-md text-2xl">
                <p>Coin</p>
                <p>Price</p>
                <p>Low (24 Hour)</p>
                <p>High (24 Hour)</p>
                <p>Market Cap</p>
            </div>
            <div v-for="(value, index) in cryptos" :key="index">
                <div
                    class="grid grid-cols-5 grid-rows-2 bg-emerald-500 bg-opacity-50 rounded-md p-2 m-3 text-lg"
                >
                    <div>{{ index }}</div>
                    <div>{{ value.USD.PRICE }}</div>
                    <div>{{ value.USD.LOW24HOUR }}</div>
                    <div>{{ value.USD.HIGH24HOUR }}</div>
                    <div>{{ value.USD.MKTCAP }}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
//import {ref} from 'vue'
import axios from 'axios'

export default {
    name: 'cryptos',
    data: () => ({
        cryptos: [],
        errors: []
    }),

    created() {
        axios.get('https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,LTC,BAT,ADA,XLM,DOGE,ETC,UNI,LINK,ALGO,&tsyms=USD,EUR')
            .then(response => {
                this.cryptos = response.data.DISPLAY
                console.log(response.Data.Message)
            })
            .catch(e => {
                this.errors.push(e)
            })
    }
}
</script>