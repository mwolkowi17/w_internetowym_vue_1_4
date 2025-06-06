<script setup>
import { ref } from 'vue';
defineEmits(['wybor-levelu1','wybor-levelu2']);
</script>
<template>
<div class="tlo-level2" role="img" alt="plansza wyboru poziomu" aria-label="plansza wyboru poziomu"></div>
   <button class="level-one-button" @click="$emit('wybor-levelu1')" role="img" alt="ikona Level Pierwszy" aria-label="Przycisk poziom jeden"></button>
   <button class="level-two-button" @click="$emit('wybor-levelu2')"role="img" alt="ikona Level Drugi" aria-label="Przycisk poziom dwa"></button>
</template>
<style scoped>
.tlo-level2 {
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
    background-image: url("../assets/poziom2_button.png");
    background-size: 390px 130px;
    background-position: -2px -1px;
    position: absolute;
    top: 295px;
    left: 710px;
    width: 390px;
    height: 130px;
}

.level-two-button:hover {
    cursor: pointer;
}
.level-two-button:focus {
    outline: thick double #08e926;
}
</style>