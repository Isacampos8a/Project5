<script setup>
import { faker } from '@faker-js/faker'


    const firstname = faker.person.firstName();
    const lastname = faker.person.lastName();
    //formatted clock-in Time
    const clockintime = faker.date.recent();
    const clockinhours = clockintime.getHours().toString().padStart(2, '0');
    const clockinminutes = clockintime.getMinutes().toString().padStart(2, '0');
    const formattedclockintime = `${clockinhours}:${clockinminutes}`;

    //formatted clock out time
    const clockouttime = new Date(clockintime.getTime() + Math.random() * (8 * 60 * 60 * 1000));
    const clockouthours = clockouttime.getHours().toString().padStart(2, '0');
    const clockoutminutes = clockouttime.getMinutes().toString().padStart(2, '0');
    const formattedclockouttime = `${clockouthours}:${clockoutminutes}`;


</script>
    
<template>

    <div class="border border-gray-500 rounded-lg shadow bg-white h-full">
        <img class="object-fill h-480 w-960 rounded-t-lg" v-bind:src="faker.image.urlLoremFlickr({ category: 'person', height: 480, width: 960 })" alt="Random Person"/>

        <div class="p-5">
            


        <p class="text"> {{ firstname }} {{ lastname }} </p>
        <p class="">Clock-in Time: {{ formattedclockintime }}</p>
        <p class="">Clock-out Time: {{ formattedclockouttime }}</p>
        </div>

    </div>
</template>