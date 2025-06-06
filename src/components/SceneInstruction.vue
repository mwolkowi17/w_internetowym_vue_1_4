<script setup>
import { ref } from 'vue'
import { instrukcjaTekst } from '../lib/instrukcja';
defineEmits(['koniec-instrukcja'])

</script>
<template>
<!-- <div class="tlo1" aria-label="Instrukcja gry"  ></div> -->
 <div class="tlo1" :aria-label="instrukcjaTekst"  ></div>
<button class="dalej" @click="$emit('koniec-instrukcja')" role="img" alt="ikona Dalej" aria-label="Przycisk dalej"  ></button>
</template>
<style>
.tlo1{
    background-image: url("../assets/plansza_zasady_gry.png");
    background-size: 1280px 720px;
    height: 720px;
    width: 1280px;
    top:0px;
    left: 0px;
    position: absolute;
}
.dalej{
    background-image: url("../assets/przycisk_dalej_imie.png");
    background-size: 170px 75px;
    background-position: -1px -5px;
    position: absolute;
    top: 550px;
    left: 580px;
    width: 171px;
    height: 68px;
}
.dalej:hover{
    cursor: pointer;
}

.dalej:focus {
   /* border: 4px solid #08e926; */
   outline: thick double #08e926;
}
</style>
