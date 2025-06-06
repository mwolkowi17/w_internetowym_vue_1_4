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
    background-size: 1920px 1080px;
    height: 1080px;
    width: 1920px;
    top:0px;
    left: 0px;
    position: absolute;
}
.dalej{
    background-image: url("../assets/przycisk_dalej_imie.png");
    background-size: 301px 117px;
    background-position: -1px -1px;
    position: absolute;
    top: 820px;
    left: 850px;
    width: 301px;
    height: 117px;
}
.dalej:hover{
    cursor: pointer;
}

.dalej:focus {
   /* border: 4px solid #08e926; */
   outline: thick double #08e926;
}
</style>
