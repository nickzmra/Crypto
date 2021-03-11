<template>
  <section class="max-w-2xl mx-auto rounded bg-content-800">
    <div class="container flex items-center justify-center text-center">
      <form
        @submit.prevent
        class="flex flex-col w-full max-w-xl m-4 p-12 rounded-lg shadow-lg bg-violet-700 bg-opacity-50"
      >
        <label
          for="username"
          class="self-start text-sm font-semibold text-content-200 text-white"
          >Email</label
        >
        <input
          id="username"
          type="text"
          class="flex items-center h-12 px-4 mt-2 bg-gray-200 rounded focus:outline-none focus:ring-2"
          v-model="email"
        />
        <label
          for="password"
          class="self-start mt-3 text-sm font-semibold text-content-200 text-white"
          >Password</label
        >
        <input
          id="password"
          type="password"
          class="flex items-center h-12 px-4 mt-2 bg-gray-200 rounded focus:outline-none focus:ring-2"
          v-model="password"
        />
        <button @click="login" class="btn btn-outline mt-4">Login</button>
      </form>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { signIn } from '../helpers/useAuth'
const router = useRouter()
const login = async () => {
  try {
    await signIn(email.value, password.value)
    router.push('/')
  } catch (error) {
    console.log(error)
  }
}
const email = ref('')
const password = ref('')
</script>