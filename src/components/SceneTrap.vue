<script setup>
import { ref } from 'vue';

defineEmits(['koniec-pulapka']);

defineOptions({
  inheritAttrs: false
})

function koniecPulapki() {
    
    // Emit the event to notify the parent component that the trap has ended
    console.log("Koniec pulapki");
}   


</script>
<template>
    <div class="pulapka1" alt="plansza pułapki" role="img" aria-label="plansza pułapki"></div>
    <button class="przycisk_pulapka1" @click="$emit('koniec-pulapka');koniecPulapki()" role="img" alt="ikona dalej" aria-label="Przycisk dalej"></button>
</template>
<style scoped>
.pulapka1 {
    background-image: url("../assets/zasadzka.png");
    background-size: 606px 261px;
    background-repeat: no-repeat;
    height: 261px;
    width: 606px;
    position: absolute;
    left: 320px;
    top: 220px;
}
.przycisk_pulapka1 {
    background-image: url("../assets/przycisk_dalej_imie.png");
    background-size: 150px 65px;
    background-position: -2px -5px;
    background-repeat: no-repeat;
    height: 58px;
    width: 149px;
    position: absolute;
    left: 545px;
    top: 380px;
   
}
.przycisk_pulapka1:hover {
    cursor: pointer;
}
.przycisk_pulapka1:focus {
    outline: thick double #08e926;
}
</style>