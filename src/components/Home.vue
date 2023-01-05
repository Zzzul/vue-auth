<script setup>
import { onMounted } from "vue"
import { useAuthStore } from "../stores/auth"

const authStore = useAuthStore()

onMounted(async () => {
  await authStore.getUser()
})
</script>
<template>
  <div v-if="authStore.user">
    <h1 class="text-dark-500">{{ authStore.user?.name }}</h1>
    <h2 class="text-gray-500">{{ authStore.user?.email }}</h2>
  </div>
  <div v-else>
    <p>Go to <router-link :to="{ name: 'Login' }">Login</router-link></p>
  </div>
</template>
