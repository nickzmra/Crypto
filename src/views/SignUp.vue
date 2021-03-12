<template>
  <section class="max-w-2xl mx-auto rounded bg-content-800">
    <div class="container flex items-center justify-center text-center">
        <form @submit.prevent class="flex flex-col w-full max-w-xl m-4 p-12 rounded-lg shadow-lg bg-violet-700 bg-opacity-50">
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
      <button @click="register" class="btn btn-success mt-4">
        Sign Up
      </button>
    </form>
    </div>
  </section>
</template>

<script setup>
import { ref, defineProps } from 'vue'
import { useRouter } from 'vue-router'
import { signUp, auth } from '../helpers/useAuth'
const router = useRouter()
const register = async () => {
  try {
    await signUp(email.value, password.value)
    const user = auth().currentUser
    await user.updateProfile({ displayName: name.value })
    router.push('/')
  } catch (error) {
    console.log(error)
  }
}
const email = ref('')
const password = ref('')

defineProps({
  form: {
    type: String,
    default: 'login',
  },
})
</script>