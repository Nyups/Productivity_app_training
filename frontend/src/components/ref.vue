<script setup>
// [IMPORTING FUNCTIONALITY]
// To import a functionality like "ref, computed, ect.." we go like
import { ref } from "vue"; //ref make the data reactive

// [DECLARING REACTIVE VALUE] Goes like :
const score = ref(0); // Number example
const username = ref("Nyucleaire"); // String example
 
// [ ACCESSING REACTIVE VALUE] Goes like :
// "score.value".. for example :
score.value = 10; // Curent score value is 10 
score.value++; // Curent score value is 11
score.value -= 5; // Curent score value is 6
console.log(score.value); // Output "6" in the console

// [TO DISPLAY IT IN THE TEMPLATE] We go like :
// "{{ score }}" surrounded by the wanted element (like a <h2> for example)
// See the example with the comment "**ref** example 01"

// [CONNECTING A FUNCTION TO AN ELEMENT] goes like:
function scoreUp() {
    score.value++;
}
// It also work with argument. For example
function scoreUp10(amount) {
    score.value += amount;
}
// Then we link them (in this example a button) (See "**ref** example 02") 


// [CONDITIONAL RENDERING]
</script>

<template>
    <h2 class="title">"ref" Study</h2>
    <br>
    <!--**ref** example 01-->
    <h3>Ref example 01</h3>
    <p>Score example : {{ score }}</p>
    <p>Username example : {{ username }}</p>
    <br>
    <!--**ref** example 02-->
    <h3>Ref example 02</h3>
    <p>Classic function</p>
    <button @click="scoreUp">Score up +1</button>
    <p>function using 10 as argument</p>
    <button @click="scoreUp10(10)">Score up +10</button>

    <!-- [BINDING EXAMPLE] :
     @click="something"
     @input="something"
     @change="something"
     @submit="something"
     @keydown="something"
     @mouseenter="something"
     -->
</template>

<style scoped>
.title {
    text-align: center;
}
</style>