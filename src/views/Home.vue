<template>
    <div class="mt-8">
        <p class="text-3xl mx-auto text-center m-16 tracking-wider font-thick text-white">
      Welcome {{ user?.email || 'New User' }}
        </p>
        <img class="h-60 mx-auto" src="../assets/home.svg" alt="Home Image"/>
        <p class="text-xl text-center">I would like the home page to have a standard overview of the crypto market</p>
    </div>
</template>

<script setup>
import { user } from '../helpers/useAuth'
</script>