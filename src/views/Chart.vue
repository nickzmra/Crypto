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
<!--
    <div class="flex flex-col container mx-auto m-4 p-4">
        <p class="text-2xl text-center bg-rose-400 p-3 mb-4 rounded">Crypto Prices</p>
        <table class="min-w-max w-full table-auto">
            <thead class="justify-between">
                <tr class='bg-indigo-600'>
                    <th class="text-2xl px-16 py-2">Cryptocurrency</th>
                    <th class="text-2xl">Price (USD)</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(value, key) in cryptos">
                    <td class="bg-indigo-400 leading-normal text-center text-xl">{{key}}</td>
                    <td class="bg-indigo-300 text-center text-xl">${{value.USD}}</td>
                </tr>
            </tbody>
        </table>
    </div>
-->