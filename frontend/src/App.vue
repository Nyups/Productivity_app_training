<script setup>
import { ref } from 'vue';

import refLesson from './components/lessons/refLesson.vue';
import refExercise from './components/lessons/ref-exercise.vue';
import vfor from './components/lessons/vfor.vue';

// Lesson toggle
const pastLesson = ref(true);

function lessonSwitch() {
  pastLesson.value = !pastLesson.value
}

</script>

<template>
  <button @click="lessonSwitch">Past Lesson</button>
  <h2 class="separation" v-if="pastLesson">////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////</h2>
<refLesson v-if="pastLesson"/>
  <h2 class="separation">////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////</h2>
<ref-exercise v-if="pastLesson"/>
  <h2 class="separation">////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////</h2>
  <vfor/>
</template>
<style>
* {
  background-color: rgb(100, 172, 174);
  color: white;
}
.separation {
  text-align: center;
}
</style>