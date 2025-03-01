<script setup>
    import TimeCards from './TimeCards.vue';

</script>

<template>
    <div class="grid grid-cols-5 gap-10 p-10">
        <TimeCards v-for="card in 20" :key="card"></TimeCards>
    </div>

</template>