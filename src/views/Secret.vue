<template>
    <p
        class="text-3xl mx-auto text-center m-16 tracking-wider font-thick text-white"
    >Use this page to put random coin statistics</p>
    <img class="h-60 mx-auto" src="../assets/login.svg" alt="Home Image" />
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
                console.log(response.data.Message) // This will give you access to the full object
            })
            .catch(e => {
                this.errors.push(e)
            })
    }
}
</script>