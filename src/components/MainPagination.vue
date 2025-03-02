<script setup>
import { ref } from 'vue'
const pages = ref(10)
const activePage = ref(2)

const prevPage = () => {
    if (activePage.value > 1) {
        activePage.value--
    }
    console.log(activePage.value)

}

const nextPage = () => {
    if (activePage.value < pages.value) {
        activePage.value++
    }

    console.log(activePage.value)
}



</script>
<template>
    <div class="flex justify-center gap-4 p-8 bg-yellow-50">
        <button @click="prevPage" :disabled="activePage === 1" class="rounded-lg bg-slate-100 p-2 font-medium text-slate-800 shadow-md">PREV</button>
        <button v-for="page in pages" :key="page" class="rounded-lg bg-slate-100 p-2 font-medium text-slate-800 shadow-md" :class="page === activePage ? 'bg-yellow-300 text-slate-700' : '' " >{{ page }}</button>               
        <button @click="nextPage" :disabled="activePage === pages" class="rounded-lg bg-slate-100 p-2 font-medium text-slate-800 shadow-md">NEXT</button>
    </div>
</template>