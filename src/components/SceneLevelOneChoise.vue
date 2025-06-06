<script setup>
import { ref } from 'vue';
defineEmits(['wybor-levelu1']);
</script>

<template>
    <div class="tlo-level1"></div>
    <button class="level-one-button" @click="$emit('wybor-levelu1')"  role="img" alt="ikona Level Pierwszy" aria-label="Przycisk poziom jeden" ></button>
    <button class="level-two-button"   role="img" alt="ikona Level Drugi" aria-label="Przycisk poziom dwa" disabled ></button>
</template>

<style scoped>
.tlo-level1 {
 background-image: url("../assets/plansza_poziom1_wybor.png");
    background-size: 1920px 1080px;
    height: 1080px;
    width: 1920px;
    top:0px;
    left: 0px;
    position: absolute;
}
.level-one-button {
   background-image: url("../assets/poziom1_button.png");
    background-size: 595px 200px;
    background-position: -1px -1px;
    position: absolute;
    top: 438px;
    left: 220px;
    width: 595px;
    height: 200px;
}
.level-one-button:hover {
    cursor: pointer;
}
.level-one-button:focus {
    outline: thick double #08e926;
}

.level-two-button{
    background-image: url("../assets/poziom2_nieaktywny_popr.png");
    background-size: 595px 200px;
    background-position: -2px -1px;
    position: absolute;
    top: 438px;
    left: 1063px;
    width: 595px;
    height: 200px;
}
</style>