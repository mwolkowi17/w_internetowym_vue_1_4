<script setup>
import { ref } from 'vue';


defineEmits(['gram-dalej','koniec-gry']);
</script>

<template>
<div class="plansza-win-level-one" role="img" alt="plansza" aria-label="Plansza wygranej"></div>
<button class="gram-jeszcze-1-level-one" @click="$emit('gram-dalej')" role="img" alt="ikona Gram Jeszcze" aria-label="przycisk gram jeszcze raz"></button>
<button class="zakoncz-gre" @click="$emit('koniec-gry')" role="img" alt="ikona zakońćz grę" aria-label="przycisk zakończ grę"></button>

</template>

<style scoped>

.plansza-win-level-one {
    background-image: url("../assets/ukonczenie_poziomu1.png");
    background-size: 1920px 1080px;
    height: 1080px;
    width:1920px;
    top: 0px;
    left: 0px;
    position: absolute;
    z-index: 2;
}
.gram-jeszcze-1-level-one{
    background-image: url("../assets/gram_dalej1.png");
    background-size: 265px 98px;
    background-position: -1px -2px;
    position: absolute;
    top: 450px;
    left: 280px;
    width: 265px;
    height: 96px;
    z-index: 3;
}
.gram-jeszcze-1-level-one:hover {
    cursor: pointer;
}   
.gram-jeszcze-1-level-one:focus {
    outline: thick double #08e926;
}   
.zakoncz-gre{
    background-image: url("../assets/zakoncz_gre_button.png");
    background-size: 583px 192px;
    background-position: -1px -1px;
    position: absolute;
    top: 650px;
    left: 920px;
    width: 583px;
    height: 192px;
    z-index: 3;
}
.zakoncz-gre:hover {
    cursor: pointer;
}   
.zakoncz-gre:focus {
    outline: thick double #08e926;
}   
</style>