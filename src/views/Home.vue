<template>
    <div class="mt-8">
        <p class="text-3xl mx-auto text-center m-16 tracking-wider font-thick text-white">
      Welcome, {{ user?.displayName || 'New User' }}!
        </p>
        <img class="h-60 mx-auto" src="../assets/home.svg" alt="Home Image"/>
        <p class="text-xl text-center">Login to view content!</p>
    </div>
</template>

<script setup>
import { user } from '../helpers/useAuth'
</script>