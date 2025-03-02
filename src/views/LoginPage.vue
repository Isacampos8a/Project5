<script setup>
import { ref } from 'vue';
import { useRoute, useRouter } from 'vue-router';

import { useAuth } from '../composables/useAuth'

const { login, logout } = useAuth()

const router = useRouter()
const route = useRoute()

const username = ref('')
const password = ref('')

const logUserIn = async () => {
    if (await login(username.value, password.value)) {
        if (route.query.refirect) {
            router.push(route.query.redirect)
        } else {
            router.push({name: 'SettingsPage'})
        }
    } else {
        logout()
    }
}
</script>

<template>
    <form class="m-10 " @submit.prevent>
        <div>
            <label for="username" class="block mb-2 font-bold">Username</label>
            <input id="username" v-model="username" type="text" placeholder="Username">
        </div>
        <div>
            <label for="password" class="block mb-2 font-bold">Password</label>
            <input id="password" v-model="password" type="password" placeholder="password">
        </div>

        <button @click="logUserIn" class="bg-green-300 mt-5 px-4 py-2 border hover:bg-green-800 hover:text-white">LOGIN</button>

    </form>


</template>