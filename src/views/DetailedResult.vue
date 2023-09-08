<script setup>
import { useRoute } from 'vue-router';
import { ref } from 'vue';
import axios from 'axios';

const route = useRoute();
const id = route.params.id;
const result = ref("");

const detailedResult = async () => {
    try {
        // TO-DO:
        const detailedResponse = await axios.get(`http://localhost:8000/result/${id}`);
        return detailedResponse.data;
    }
    catch (error) {
        console.log(error.message);
    }
}
result.value = detailedResult();


</script>

<template>
    <div class="mx-14 my-7">
        <p class="font-semibold text-blue text-18">Detailed Result</p>
        <div class="grid grid-cols-4 bg-gray-50 rounded-lg mt-7 py-2 px-7 items-center text-base text-blue text-md">
            <div class="col-span-1 font-medium text-sm">
                ID
            </div>
            <div class="col-span-1 font-medium text-sm">
                Name
            </div>
            <div class="col-span-1 font-medium text-sm">
                Features
            </div>
            <div class="col-span-1 font-medium text-sm">
                Percentage of Credit Default
            </div>
        </div>
        <div class="grid grid-cols-4 bg-gray-25 rounded-sm py-2 px-7 items-center text-base text-blue">
            <div class="col-span-1 font-normal text-base">
                {{ result.value.id }}
            </div>
            <div class="col-span-1 font-normal text-base">
                {{ result.value.name }}
            </div>
            <div class="col-span-1 font-normal text-base">
               
            </div>
            <div class="col-span-1 font-normal text-base">
                {{ result.value.percentage }}%
            </div>
        </div>
    </div>
</template>
