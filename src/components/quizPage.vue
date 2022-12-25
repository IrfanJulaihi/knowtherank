<template>
    <h1>Guess the rank</h1>

    <!-- success modal -->

    
        <div v-if="answer=='correct'" class="flex justify-center items-center w-full   bg-gray-600 bg-opacity-50   ">
        <div class="shadow-lg  rounded-md bg-white">
            <div class="mt-8 text-center">
                <div class="mx-auto flex items-center justify-center h-12 w-12 rounded-full bg-green-100">
                    <svg class="h-6 w-6 text-green-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        xmlnx="http://www.w.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7">
                        </path>
                    </svg>
                </div>
                <h3 class="text-lg leading-6 font-medium text-gray-900">Correct</h3>
                <div class="mt-2 px-7 py-3">
                    <p class="text-sm text-gray-500">You deserve a salute.</p>
                </div>
                <div class="items-center px-4 py-3">
                    <button @click="answer = !answer" class="px-4 py-2 bg-green-500 text-white
                            text-base font-medium rounded-md w-full
                            shadow-sm hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-300">
                        OK
                    </button>
                </div>
            </div>
        </div>
    </div>

    <div v-else-if="answer=='wrong'" class="flex justify-center items-center w-full   bg-gray-600 bg-opacity-50   ">
        <div class="shadow-lg  rounded-md bg-white">
            <div class="mt-8 text-center">
                <div class="mx-auto flex items-center justify-center h-12 w-12 rounded-full bg-red-100">
                    <svg class="h-6 w-6 text-red-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                        xmlnx="http://www.w.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7">
                        </path>
                    </svg>
                </div>
                <h3 class="text-lg leading-6 font-medium text-gray-900">Correct</h3>
                <div class="mt-2 px-7 py-3">
                    <p class="text-sm text-gray-500">Wrong try again.</p>
                </div>
                <div class="items-center px-4 py-3">
                    <button @click="answer = !answer" class="px-4 py-2 bg-red-500 text-white
                            text-base font-medium rounded-md w-full
                            shadow-sm hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-300">
                        OK
                    </button>
                </div>
            </div>
        </div>
    </div>

    <div v-else class="grid-container ">
        <div v-for="ans in options" class="rectangle" @click="checkAnswer(ans)" @mouseover="" style="cursor: pointer;">
            {{ ans }} </div>

    </div>




</template>
<script setup>

import { onMounted, ref } from 'vue'


const props = defineProps(['title'])
const count = ref(0)
const answer = ref(false)
const options
    = ref(['Fil Marsyal', 'Jeneral', 'Leftenan Jeneral', 'Mejar Jeneral', 'Brigadier Jeneral', 'Kolonel', 'Leftenan Kolonel', 'Mejar', 'Kapten', 'Leftenan', 'Leftenan Muda',])


onMounted(() => {

    shuffle(options
        .value)
})

//Function to reshuffle the array
function shuffle(array) {
    var copy = [], n = array.length, i;

    // While there remain elements to shuffle…
    while (n) {

        // Pick a remaining element…
        i = Math.floor(Math.random() * n--);

        // And move it to the new array.
        copy.push(array.splice(i, 1)[0]);
    }
    options
        .value = copy

}

function checkAnswer(val) {

    if (val == props.title) {
        answer.value='correct'
        setTimeout(()=>{
            window.location.reload()
        },1000)
     

    } else {
     answer.value='wrong'

    }
}
</script>
<style>
.rectangle {
    height: 40px;
    width: 300px;
    background-color: #555;
    border: 1px solid rgba(0, 0, 0, 0.8);
    padding: 10px;
    margin-inline: 20px;
    margin-block-end: 10px;
    margin-block-start: 10px;
    font-size: 20px;
    text-align: center;

}

.grid-container {
    display: grid;
    grid-template-columns: auto auto;
    background-color: #2196F3;
    padding: 10px;
    column-gap: 10px;
}
</style>