<template>
    <div class="flex flex-col container mx-auto min-h-screen">
        <h1 class="text-4xl text-center text-white font-bold mt-4 mb-8">Crypto Prices</h1>
        <table class="table-auto">
            <thead>
                <tr class="bg-green-400 bg-opacity-40">
                    <th class="text-lg p-4">Coin</th>
                    <th class="text-lg">Price (USD)</th>
                    <th class="text-lg">Market Cap</th>
                    <th class="text-lg">High (24 Hour)</th>
                    <th class="text-lg">Low (24 Hour)</th>
                </tr>
            </thead>
            <tbody
                class="bg-blueGray-400 bg-opacity-60"
                v-for="(value, index) in cryptos"
                :key="index"
            >
                <tr>
                    <td class="text-2xl p-3 m-2">{{ value.USD.FROMSYMBOL }}</td>
                    <td class="text-2xl">{{ value.USD.PRICE }}</td>
                    <td class="text-2xl">{{ value.USD.MKTCAP }}</td>
                    <td class="text-2xl">{{ value.USD.HIGH24HOUR }}</td>
                    <td class="text-2xl">{{ value.USD.LOW24HOUR }}</td>
                </tr>
            </tbody>
        </table>
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
        axios.get('https://min-api.cryptocompare.com/data/pricemultifull?fsyms=BTC,ETH,LTC,BAT,ADA,XLM,DOGE,UNI,LINK,ALGO,&tsyms=USD,EUR')
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