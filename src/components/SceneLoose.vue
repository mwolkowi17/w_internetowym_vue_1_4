<script setup>
import { ref } from 'vue';
defineEmits(['jeszcze-raz','koniec-gry']);
</script>

<template>
    <div class="plansza-lose" role="img" alt="plansza" aria-label="Plansza przegranej"></div>
    <button class="gram-jeszcze-1" @click="$emit('jeszcze-raz')" role="img" alt="ikona Gram Jeszcze" aria-label="przycisk gram jeszcze raz"></button>
    <button class="zakoncz-gre" @click="$emit('koniec-gry')" role="img" alt="ikona zakońćz grę" aria-label="przycisk zakończ grę"></button>
</template>

<style scoped>
.plansza-lose {
    background-image: url("../assets/przegrana_plansza.png");
    background-size: 1280px 720px;
    height: 720px;
    width: 1280px;
    top: 0px;
    left: 0px;
    position: absolute;
    z-index: 2;
}
.gram-jeszcze-1{
    background-image: url("../assets/gram_jeszcze_raz_button.png");
    background-size: 265px 98px;
    background-position: -1px -2px;
    position: absolute;
    top: 450px;
    left: 280px;
    width: 265px;
    height: 96px;
    z-index: 3;
}

.gram-jeszcze-1:hover {
    cursor: pointer;
}
.gram-jeszcze-1:focus {
    outline: thick double #08e926;
}
.zakoncz-gre{
    background-image: url("../assets/zakoncz_gre_button.png");
    background-size: 265px 98px;
    background-position: -1px -2px;
    position: absolute;
    top: 450px;
    left: 720px;
    width: 265px;
    height: 96px;
    z-index: 3;
}
.zakoncz-gre:hover {
    cursor: pointer;
}

.zakoncz-gre:focus {
    outline: thick double #08e926;
}
</style>