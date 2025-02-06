<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { useUserStore } from '@/stores'
import CONSTANTS from '@/CONSTANTS'

const router = useRouter()
const userStore = useUserStore()

const email = ref('')
const password = ref('')
const isLoading = ref(false)
const errorMessage = ref('')

const handleLogin = async () => {
  isLoading.value = true
  errorMessage.value = ''

  try {
    const payload = { Email: email.value, Password: password.value }
    const res = await userStore.login(payload)
    if (res) {
      await router.push({ path: CONSTANTS.routes.dashboard })
    }
  } catch (err) {
    errorMessage.value = 'Invalid email or password. Please try again.'
    console.log(err)
  } finally {
    isLoading.value = false
  }
}
</script>

<template>
  <div class="bg-white p-8 rounded-lg shadow-lg w-full max-w-md mx-auto">
    <GetErrorSuccess />
    <h2 class="text-3xl font-semibold mb-6 text-center text-gray-800">Login 👋</h2>
    <form @submit.prevent="handleLogin">
      <div class="mb-5">
        <label
          for="email"
          class="block text-gray-700 font-medium mb-2"
        >
          Email 💌
        </label>
        <input
          id="email"
          v-model="email"
          class="w-full px-4 py-3 border border-gray-100 rounded-lg focus:outline-none focus:ring-1 focus:ring-[#5f28c7] transition duration-200 bg-white text-gray-700 placeholder-gray-500"
          type="email"
          required
          placeholder="Enter your email"
        />
      </div>

      <div class="mb-6">
        <label
          for="password"
          class="block text-gray-700 font-medium mb-2"
        >
          Password 👁

        </label>
        <input
          id="password"
          v-model="password"
          class="w-full px-4 py-3 border border-gray-100 rounded-lg focus:outline-none focus:ring-1 focus:ring-[#5f28c7] transition duration-200 bg-white text-gray-700 placeholder-gray-500"
          type="password"
          required
          placeholder="Enter your password"
        />
      </div>

      <!-- Error message -->
      <div v-if="errorMessage" class="mb-4 text-red-600 text-sm text-center">
        {{ errorMessage }}
      </div>

      <button
        :disabled="isLoading"
        class="w-full bg-gradient-to-r from-[#7a4dff] via-[#5f28c7] to-[#6525fb] text-white py-3 rounded-lg hover:bg-gradient-to-r hover:from-[#6525fb] hover:via-[#5f28c7] hover:to-[#7a4dff] transition duration-300 ease-in-out relative flex items-center justify-center"
      >
        <span v-if="!isLoading">Submit</span>
        <svg
          v-if="isLoading"
          class="animate-spin h-5 w-5 text-white"
          fill="none"
          viewBox="0 0 24 24"
        >
          <circle
            class="opacity-25"
            cx="12"
            cy="12"
            r="10"
            stroke="currentColor"
            stroke-width="4"
          ></circle>
          <path
            class="opacity-75"
            fill="currentColor"
            d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4z"
          ></path>
        </svg>
      </button>
    </form>
  </div>
</template>
