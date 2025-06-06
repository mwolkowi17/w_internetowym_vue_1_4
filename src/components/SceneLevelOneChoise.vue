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
    background-size: 1280px 720px;
    height: 720px;
    width: 1280px;
    top:0px;
    left: 0px;
    position: absolute;
}
.level-one-button {
   background-image: url("../assets/poziom1_button.png");
    background-size: 390px 130px;
    background-position: -2px -1px;
    position: absolute;
    top: 295px;
    left: 180px;
    width: 390px;
    height: 130px;
}
.level-one-button:hover {
    cursor: pointer;
}
.level-one-button:focus {
    outline: thick double #08e926;
}

.level-two-button{
    background-image: url("../assets/poziom2_nieaktywny_popr.png");
    background-size: 392px 130px;
    background-position: -2px -1px;
    position: absolute;
    top: 295px;
    left: 712px;
    width: 392px;
    height: 130px;
}
</style>