<script setup>
import { ref } from 'vue';

// [LIGHT SWITCH]
const light = ref(false);
const status = ref("Off")

function lightSwitch() {
    light.value = !light.value;
    if(light.value) {
        status.value = "On"
    } else {
        status.value = "Off"
    }
}

// [RPG HEALTH SYSTEM]
const knightHealth = ref(100);
const knightStatus = ref("Healthy");

function damage(amount) {
    knightHealth.value -= amount;
    if (knightHealth.value <= 0) {
    knightStatus.value = "You got slimmed twin.";
} else if (knightHealth.value < 30) {
    knightStatus.value = "You are critically injured";
} else if (knightHealth.value < 70) {
    knightStatus.value = "You are injured.";
} else {
    knightStatus.value = "Healthy";
}
}

function healing(amount) {
    knightHealth.value += amount;
    if (knightHealth.value <= 0) {
    knightStatus.value = "You got slimmed twin.";
} else if (knightHealth.value < 30) {
    knightStatus.value = "You are critically injured";
} else if (knightHealth.value < 70) {
    knightStatus.value = "You are injured.";
} else {
    knightStatus.value = "Healthy";
}
}
// note : The status are raw coded but at least I learned that I had to store the if else
// in the function for them to work properly...

// [TINY VIRTUAL PET]
const petName = ref("Pich");
const petHunger = ref(100);
const petHappy = ref(30);
const petSleep = ref(false);
const sleepStatus = ref("No");


function play() {
    if(petSleep.value) {
        return
    } else {
    petHunger.value += 5;
    petHappy.value += 10;
    if(petHunger.value > 100) {
        petHunger.value = 100;
    }
    if(petHappy.value > 100) {
        petHappy.value = 100;
    }
    }
}

function feed() {
    if(petSleep.value) {
        return
    } else {
    petHunger.value -= 10;

    if(petHunger.value < 0) {
        petHunger.value = 0;
    }
    }
}

function sleepingPet() {
    petSleep.value = !petSleep.value;
    if(petSleep.value) {
        sleepStatus.value = "Yes";
    } else {
        sleepStatus.value = "No";
    }
}
</script>

<template>
    <h2 class="heading">"ref" Exercise Component</h2>
    <br>
    <!--Light switch-->
    <h3>Light Switch exercise</h3>
    <p>status: {{ status }}</p>
    <button @click="lightSwitch">Turn On/Off</button>
    <p v-if="light">The light is on yay!</p>
    <p v-else>It's all dark.</p>
    <br>

    <!--RPG health system-->
    <h3>RPG Health system exercise</h3>
    <p>HP: {{ knightHealth }}</p>
    <p>Status : {{ knightStatus }}</p>
    <Button @click="damage(10)">-10 HP</Button>
    <br>
    <Button @click="damage(25)">-25 HP</Button>
    <br>
    <Button @click="healing(20)">+20 HP</Button>
    <br>

    <!--Tiny virtual pet-->
    <h3>Tiny virtual pet</h3>
    <div>
    <div class="">
        <button @click="feed">Feed</button>
        <button @click="play">Play</button>
        <button @click="sleepingPet">Sleep / Wake up</button>
    </div>

    <div>
    <p>Name : {{ petName }}</p>

    <p>Hunger : {{ petHunger }}</p>
    <p v-if="petHunger >= 80 ">{{ petName }} is feeling hungry!</p>
    <p v-else-if="petHunger <= 80">Is feeling fine</p>
    <br>

    <p>Hapiness : {{ petHappy }}</p>
    <p v-if="petHappy <= 20">{{ petName }} is feeling pretty sad.</p>
    <p v-else>is feeling pretty good!</p>
    <br>

    <p>Sleeping : {{ sleepStatus }}</p>
    <p v-if="petSleep"> {{ petName }} is sleeping...</p>
    <p v-else>{{ petName }} is wide awake</p>
    </div>

    </div>
</template>

<style scoped>
.heading {
    text-align: center;
}
</style>