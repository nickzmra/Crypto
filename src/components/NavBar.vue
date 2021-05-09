<template>
  <nav
    class="navbar mb-2 shadow-lg bg-content-800 text-content-100 bg-trueGray-800 bg-opacity-80 text-white"
  >
    <div class="flex-1 px-6 m-2">
      <span
        class="text-3xl text-transparent bg-gradient-to-l from-pink-500 via-violet-500 to-cyan-400 font-semibold bg-clip-text"
      >crypto</span>
    </div>
    <div class="flex-none flex px-2 mx-2">
      <div class="flex">
        <router-link to="/" class="btn btn-ghost btn-sm rounded-btn hover:text-content-100">Coins</router-link>

        <div v-if="!isAuthenticated">
          <router-link
            to="/login"
            class="btn btn-ghost btn-sm rounded-btn hover:text-content-100"
          >Login</router-link>
          <router-link
            to="/signup"
            class="btn btn-ghost btn-sm rounded-btn hover:text-content-100"
          >SignUp</router-link>
        </div>
        <div v-else>
          <router-link
            to="/charts"
            class="btn btn-ghost btn-sm rounded-btn hover:text-content-100"
          >Chart</router-link>
          <router-link
            to="/news"
            class="btn btn-ghost btn-sm rounded-btn hover:text-content-100"
          >News</router-link>
          <router-link
            to="/secret"
            class="btn btn-ghost btn-sm rounded-btn hover:text-content-100"
          >Pairs</router-link>
          <button
            class="btn btn-error btn-sm rounded-btn hover:text-content-100"
            @click="logout"
          >Logout</button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { isAuthenticated, signOut } from '../helpers/useAuth.js'
import { isError } from '../helpers/useError'

const router = useRouter()
const logout = async () => {
  await signOut()
  router.push('/')
}
</script>

