<template>
  <div class="mt-8">
    <h1
      class="text-3xl mx-auto text-center m-2 tracking-wider font-thick text-white"
    >Welcome, {{ user?.displayName || 'New User' }}!</h1>
    <p class="text-center text-white m-8">Login to View Content!</p>
    <img class="h-60 mx-auto" src="../assets/home.svg" alt="Home Image" />
  </div>
</template>

<script setup>
import { user } from '../helpers/useAuth'
</script>