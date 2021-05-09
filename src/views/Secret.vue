<template>
    <div class="container flex flex-col mx-auto min-h-screen">
        <p
            class="text-3xl mx-auto text-center m-6 tracking-wider font-thick text-white"
        >More Coin Data</p>
        <p class="text-white text-center items-justify">Vol:</p>
        <div v-for="(coin, index) in coins" :key="index">
            <div class="container flex flex-col justify-between mx-auto text-white">
                <p
                    class="text-justify m-2 rounded-md bg-coolGray-600 p-4"
                >{{ coin.cccagg_volume_base }} {{ coin.time }}</p>
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
        axios.get('https://min-api.cryptocompare.com/data/symbol/histohour?fsym=BTC&tsym=USD&limit=10')
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