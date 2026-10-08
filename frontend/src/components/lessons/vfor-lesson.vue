<script setup>
import { ref } from 'vue';

// [OUR FIRST V-FOR] [Example-01]
// With a simple array like this one :
const items = ["Potion","Sword","Shield"];
// We can loop through that array directly in our template.


// [USING "v-for" WITH "ref()"] [Example 02]
// basically the same exept our array look like this with "ref()" :
const items02 = ref(["Salad","Tomato",'oignon']);
// though we wtill have to use the .value to manipulate it like so for example:
items02.value.push("bread");
// and vue will automatically update and display the full array in the template thanks to "v-for". 

// [Distinction to remember] :
// In JavaScript: "items.value"
// In Template : "items"
// Repeating an element : v-for="item in items"


// [LOOPING THROUGH OBJECTS] [Example 03]
// Supposing we have a task list like this one :
const tasks = ref([
    {id: 1,name: "Study HTML", done: "true"},
    {id: 2,name: "Learn Vue", done: "false"},
    {id: 3,name: "Practice JavaScript", done: "false"}
]);
// Each element is an object with Two properties : "name" and "done".
// We can still use the "v-for" the exact same way : (see at the matching template example)


// [GETTING THE INDEX OF AN ITEM] [Example 04]
// For that, v-for support a second variable :
//        <li v-for="(potato, index) in items"> 
//            {{ index }} - {{ potato }}
//        </li>



// [THE ":key" ATTRIBUTE] [Example 05]
// Vue need to identify individual elements in a rendered list so it can efficiently track changes
// when items are added, removed or re-ordered. 
// The ":key" give each rendered items a stable identity.
// For an array of unique string, using the :key="item" can work.
// However for an array of object, a unique ID is usually better:
const taskExample = ref([
    {id: 1, name: "task01"},
    {id: 2, name: "task02"},
    {id: 3, name: "task03"}
]);
// Then in the template we go like :
// <div v-for="task in taskExample" :key="task.id" >
// {{ taskExample.name }}
// </div>




// [TESTING AREA]

</script>

<template>
    <h1 class="heading">V-for lesson</h1>

    <!--[Example-01] (v-for)-->
    <h2>V-for example 01 (v-for)</h2>
    <ul>
        <!-- 
        -"v-for": tells Vue to repeat an element 
        -"potato": is the temporary variable representing the current element of the array and can be nammed anything.
        -"in items": tells Vue which array to loop through.
        -"{{ potato }}": Display the current value in the template / HTML.

        Basically our little code is saying:  
        "For every item(or potato in our case), create one <li> and display that item."
        -->
        <li v-for="(potato, index) in items"> 
            {{ index }} - {{ potato }}
        </li>
        <br>
    </ul>
    <br>

    <!--[Example 02] (v-for with ref)-->
    <h2>V-for example 02 (v-for with ref())</h2>
    <ul>
        <li v-for="ingredients in items02">
            {{ ingredients }}
        </li>
    </ul>
    <br>

    <!--[Example 03] (Looping through object)-->
    <h2>V-for example 03 (Looping through object)</h2>
    <div v-for="task in tasks">
        <p>{{ task.name }}</p>
        <p>{{ task.done }}</p>
        <br>
    </div>


<!-- [TESTING AREA] -->
 <h2>Testing area</h2>
</template>

<style scoped>
.heading {
    text-align: center;
}
</style>