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
    let clockouttime = new Date(clockintime.getTime() + Math.random() * (8 * 60 * 60 * 1000));

    //makes sure the clockout time is After the clockin time
    if (clockouttime < clockintime) {
        const temp = clockintime;
        clockintime = clockouttime;
        clockouttime = temp;
    }

    const clockouthours = clockouttime.getHours().toString().padStart(2, '0');
    const clockoutminutes = clockouttime.getMinutes().toString().padStart(2, '0');
    const formattedclockouttime = `${clockouthours}:${clockoutminutes}`;

    const breaktimeinminutes = 30;

    //foramtted Time duration
    let durationMilliseconds = clockouttime - clockintime; 

    const mininmunDurationMilliseconds = 3 * 60 * 60 * 1000;

    //makes sure is no less than 3 hours
    if (durationMilliseconds < mininmunDurationMilliseconds) {
        const additionalTime = mininmunDurationMilliseconds - durationMilliseconds;
        clockouttime = new Date(clockouttime.getTime() + additionalTime)
        durationMilliseconds = clockouttime - clockintime;
    }

    const breaktimemilliseconds = breaktimeinminutes * 60 * 1000;
    const adjustedDurationMilliseconds = durationMilliseconds - breaktimemilliseconds
    const durationhours = Math.floor(adjustedDurationMilliseconds / (1000 * 60 * 60));
    const durationminutes = Math.floor((adjustedDurationMilliseconds % (1000 * 60 * 60)) / (1000 * 60));
    const formattedduration = `${durationhours}h ${durationminutes}m`


</script>
    
<template>

    <div class="border border-gray-500 rounded-3xl shadow bg-white h-full">
        <img class="object-fill h-480 w-960 rounded-t-3xl" v-bind:src="faker.image.urlLoremFlickr({ category: 'person', height: 480, width: 960 })" alt="Random Person"/>

        <div class="p-5">
            


        <p class="mb-2 text-2x1 font-bold"> {{ firstname }} {{ lastname }} </p>
        <p class="mb-3 font-normal text-gray-800">Clock-in Time: {{ formattedclockintime }}</p>
        <p class="mb-3 font-normal text-gray-800">Clock-out Time: {{ formattedclockouttime }}</p>
        <p class="mb-3 font-normal text-gray-800">Break Time (in Minutes): {{ breaktimeinminutes }}</p>
        <p class="mb-3 font-normal text-gray-800">Time Duration: {{ formattedduration }}</p>

        </div>

    </div>
</template>