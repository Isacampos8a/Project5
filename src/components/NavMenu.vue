<script setup>
import { useAuth } from '../composables/useAuth';
const {isAuthenticated, logout, user } = useAuth()
</script>

<template >
  <nav class="bg-yellow-200 p-5 ">
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/other">Other</RouterLink>
    <RouterLink to="/Settings">Settings</RouterLink>

    <div v-if="isAuthenticated">
      Welcome {{ user.email }}
      <button @click="logout" class="bg-red-500 px-4 py-2 mx-2 text-white hover:bg-red-800">LOGOUT</button>
    </div>
    <div v-else>
      <RouterLink to="/login">Login</RouterLink>

    </div>


  </nav>
</template>

<style lang="postcss" scoped>
nav {
  @apply flex justify-center space-x-4;

  & .router-link-active {
    @apply underline underline-offset-4;
  }
}
</style>
