<template>
    <div class="flex flex-col container mx-auto">
        <p class="text-3xl text-center font-bold bg-rose-400 p-3 mb-4 rounded shadow-2xl">Crypto Prices</p>
        <table class="table-auto">
            <thead class="">
                <tr class='bg-indigo-600'>
                    <th class="text-2xl">Cryptocurrency</th>
                    <th class="text-2xl">Price (USD)</th>
                </tr>
            </thead>
            <tbody class="justify-between">
                <tr v-for="(value, key) in cryptos" class="bg-cyan-800">
                    <td class="text-xl">{{key}}</td>
                    <td class="text-xl">${{value.USD}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    //import {ref} from 'vue'
    import axios from 'axios'

    export default {
        name: '',
        data: () => ({
            cryptos: [],
            errors: []
        }),

        created () {
            axios.get('https://min-api.cryptocompare.com/data/pricemulti?fsyms=BTC,ETH,LTC,BAT,ADA,XLM,DOGE,UNI,LINK,ALGO,&tsyms=USD')
            .then(response => {
                this.cryptos = response.data
                console.log(response)
            })
            .catch(e => {
                this.errors.push(e)
            })
        }
    }
</script>