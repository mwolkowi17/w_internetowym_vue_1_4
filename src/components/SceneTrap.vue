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
    <div class="pulapka1" alt="cofasz się o dwa pola" role="img" aria-label="Zasadzka - cofasz się dwa pola"></div>
    <button class="przycisk_pulapka1 anim1" @click="$emit('koniec-pulapka');koniecPulapki()" role="img" alt="ikona dalej" aria-label="Przycisk dalej"></button>
</template>
<style scoped>
.pulapka1 {
    background-image: url("../assets/zasadzka.png");
    background-size: 1212px 533px;
    background-repeat: no-repeat;
    height:533px;
    width: 1212px;
    position: absolute;
    left: 100px;
    top: 250px;
}
.przycisk_pulapka1 {
    background-image: url("../assets/przycisk_dalej_imie.png");
    background-size: 301px 117px;
    background-position: -1px -2px;
    background-repeat: no-repeat;
    height: 117px;
    width: 301px;
    position: absolute;
    left: 545px;
    top: 590px;
   
}
.przycisk_pulapka1:hover {
    cursor: pointer;
}
.przycisk_pulapka1:focus {
    /* outline: thick double #08e926; */
    outline: 8px solid #08e926;
}

/* The animation code */
@keyframes example {
  /* from {background-color: red;}
  to {background-color: yellow;} */
  from {opacity: 0;}
  to {opacity: 100;}
}

/* The element to apply the animation to */
.anim1 {
  
  animation-name: example;
  animation-duration: 1s;
}
</style>