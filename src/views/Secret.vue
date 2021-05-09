<template>
    <div class="container mx-auto min-h-screen">
        <h1
            class="text-3xl text-center mt-4 mb-8 tracking-wider font-thick text-white"
        >Top 25 Bitcoin Trading Pairs</h1>

        <div class="text-xl grid grid-cols-5 text-white mb-8 bg-emerald-600 rounded-md p-4 m-3">
            <div>Previous</div>
            <div>
                <ic:round-arrow-right-alt />
            </div>
            <div>New</div>
            <div>Volume (24 Hour)</div>
            <div>Price</div>
        </div>
        <div v-for="(coin, index) in coins" :key="index">
            <div
                class="grid grid-cols-5 grid-rows-2 text-white bg-blueGray-500 bg-opacity-50 rounded-lg p-3 m-4"
            >
                <div>{{ coin.fromSymbol }}</div>
                <div>
                    <ic:round-arrow-right-alt />
                </div>
                <div>{{ coin.toSymbol }}</div>
                <div>{{ Math.round(coin.volume24hTo) }}</div>
                <div>${{ coin.price }}</div>
            </div>
        </div>
    </div>
</template>


<script>
import axios from 'axios'
export default {
    name: 'coins',
    data: () => ({
        coins: [],
        errors: []
    }),
    created() {
        axios.get('https://min-api.cryptocompare.com/data/top/pairs?fsym=BTC&limit=15')
            .then(response => {
                this.coins = response.data.Data
                console.log(response.data.Message)
            })
            .catch(e => {
                this.errors.push(e)
            })
    }
}
</script>