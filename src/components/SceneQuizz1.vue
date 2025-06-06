<script setup>
import { ref } from 'vue';
import { Quests } from '../lib/quests-source.js';

defineOptions({
  inheritAttrs: false
})

const props = defineProps({
  miejsceNaPlanszy: Number,
  msg: String
});
const emit = defineEmits(['koniec-quizz',
  'odejmij-szanse']);

let nr_zestawu = Math.floor(Math.random() * 2);

console.log(props.msg);
console.log(props.miejsceNaPlanszy);

const quizz_assets_data = new Quests();



const is_krzyzyk1 = ref(false);
const is_krzyzyk2 = ref(false);
const if_button_dalej = ref(false);
const if_odpowiedz_dobrze = ref(false);
const if_button_dalej_dobrze = ref(false);
const if_odpowiedz_zle = ref(false);
const if_button_dalej_zle = ref(false);
const czy_odpowiedz_poprawna = ref(false);
const czy_odpowiedz_zla = ref(false);


const eksp1 = [
  "planszaQuizz1nr1",
  "planszaQuizz1nr2",
  "planszaQuizz1nr3",
  "planszaQuizz1nr4",
  "planszaQuizz1nr5",
  "planszaQuizz1nr6",
  "planszaQuizz1nr7",
  "planszaQuizz1nr8",
  "planszaQuizz1nr9",
  "planszaQuizz1nr10"
]

function zaznaczenie1() {
  console.log("Zaznaczenie 1");
  if (quizz_assets_data.pokaz_zadanie_2(props.miejsceNaPlanszy).odpowiedz_text[nr_zestawu][2] === 1) {
    console.log("Odpowiedź poprawna");
    czy_odpowiedz_poprawna.value = true;
    czy_odpowiedz_zla.value = false;

  } else {
    console.log("Odpowiedź zła");
    czy_odpowiedz_poprawna.value = false;
    czy_odpowiedz_zla.value = true;
  }
}

function zaznaczenie2() {
  console.log("Zaznaczenie 2");
  if (quizz_assets_data.pokaz_zadanie_2(props.miejsceNaPlanszy).odpowiedz_text[nr_zestawu][2] === 2) {
    console.log("Odpowiedź poprawna");
    czy_odpowiedz_poprawna.value = true;
    czy_odpowiedz_zla.value = false;
  } else {
    console.log("Odpowiedź zła");
    czy_odpowiedz_poprawna.value = false;
    czy_odpowiedz_zla.value = true;
  }
}

function sprawdzOdpowiedz() {
  console.log("Sprawdzam odpowiedź");
  if (czy_odpowiedz_poprawna.value) {
    console.log("Odpowiedź poprawna!!!!");
    if_odpowiedz_dobrze.value = true;
    if_button_dalej_dobrze.value = true;
    if_button_dalej.value = false;
    is_krzyzyk1.value = false;
    is_krzyzyk2.value = false;

  } else {
    console.log("Odpowiedź zła!!!!");
    if_odpowiedz_zle.value = true;
    if_button_dalej_zle.value = true;
    if_button_dalej.value = false;
    is_krzyzyk1.value = false;
    is_krzyzyk2.value = false;
    emit('odejmij-szanse');
  }
}

</script>
<template>
  <div class="planszaQuizz1 " :class="eksp1[quizz_assets_data.pokaz_zadanie_2(props.miejsceNaPlanszy).pytanie]"
    alt="quizz" aria-label="plansza quizzu"></div>

  <p class="pytanie1 anim1">{{ quizz_assets_data.pokaz_zadanie_2(props.miejsceNaPlanszy).tresc }}</p>
  <div class="krzyzyk" :class="{ 'krzyzyk1': is_krzyzyk1, 'krzyzyk2': is_krzyzyk2 }" role="img" alt="zaznaczenie odpowiedzi"
    aria-label="zaznaczona odpowiedź"></div>
  <button class="pole-zazn pole1 anim1" @click="is_krzyzyk1 = true,
    is_krzyzyk2 = false,
    if_button_dalej = true,
    zaznaczenie1()" role="img" alt="pole zaznaczenia"
    aria-label="zaznacz odpowiedź 1"></button>

  <p class="odpowiedz odpowiedz1 anim1">{{
    quizz_assets_data.pokaz_zadanie_2(props.miejsceNaPlanszy).odpowiedz_text[nr_zestawu][0] }}</p>
  <button class="pole-zazn pole2 anim1" @click="is_krzyzyk2 = true,
    is_krzyzyk1 = false,
    if_button_dalej = true,
    zaznaczenie2()" role="img" alt="pole zaznaczenia"
    aria-label="zaznacz odpowiedź 2"></button>
  <p class="odpowiedz odpowiedz2 anim1">{{
    quizz_assets_data.pokaz_zadanie_2(props.miejsceNaPlanszy).odpowiedz_text[nr_zestawu][1] }}</p>
  <button class="button-dalej" v-if="if_button_dalej" @click="sprawdzOdpowiedz()" role="img" alt="przycisk sprawdź"
    aria-label="przycisk sprawdź odpowiedź"></button>
  <div class="plansza-dobrze" v-if="if_odpowiedz_dobrze" role="img" alt="plansza dobra odpowiedź"
    aria-label="plansza odpowiedź prawidłowa"></div>
  <button class="button-dalej-dobrze" v-if="if_button_dalej_dobrze" @click="if_odpowiedz_dobrze = false,
    if_button_dalej_dobrze = false,
    $emit('koniec-quizz')" role="img"
    alt="przycisk dalej" aria-label="przycisk dalej - powrót do gry"></button>
  <div class="plansza-zle" v-if="if_odpowiedz_zle" role="img" alt="plansza zła odpowiedź"
    aria-label="plansza odpowiedź nieprawidłowa"></div>
  <button class="button-dalej-dobrze" v-if="if_button_dalej_zle" @click="if_odpowiedz_zle = false,
    if_button_dalej_zle = false,
    $emit('koniec-quizz')" role="img"
    alt="przycisk dalej" aria-label="przycisk dalej - powrót do gry"></button>


</template>
<style scoped>
.planszaQuizz1 {

  background-size: 935px 600px;
  background-repeat: no-repeat;
  height: 600px;
  width: 935px;
  position: absolute;
  left: 0px;
  top: 60px;
}

.planszaQuizz1nr1 {
  background-image: url("../assets/pytanie1.png");
}

.planszaQuizz1nr2 {
  background-image: url("../assets/pytanie2.png");
}

.planszaQuizz1nr3 {
  background-image: url("../assets/pytanie3.png");
}

.planszaQuizz1nr4 {
  background-image: url("../assets/pytanie4.png");
}

.planszaQuizz1nr5 {
  background-image: url("../assets/pytanie5.png");
}

.planszaQuizz1nr6 {
  background-image: url("../assets/pytanie6.png");
}

.planszaQuizz1nr7 {
  background-image: url("../assets/pytanie7.png");
}

.planszaQuizz1nr8 {
  background-image: url("../assets/pytanie8.png");
}

.planszaQuizz1nr9 {
  background-image: url("../assets/pytanie9.png");
}

.planszaQuizz1nr10 {
  background-image: url("../assets/pytanie10.png");
}


.pytanie1 {
  color: rgb(29, 56, 80);
  font-size: 30px;
  font-style: bold;
  font-weight: 700;
  font-family: "Proxima Nova", sans-serif;
  position: absolute;
  top: 195px;
  left: 124px;
}

.pole-zazn {
  /* background-image: url("../assets/kratka.png");
  background-size: 50px 50px;
  background-repeat: no-repeat; */
  border: rgb(29, 56, 80) solid 2px;
  height: 50px;
  width: 50px;
  position: absolute;

}

.pole-zazn:hover {
  cursor: pointer;
}

.pole-zazn:focus {
  outline: thick double #08e926 !important;
}

.pole1 {
  left: 130px;
  top: 305px;
}

.pole2 {
  left: 130px;
  top: 385px;
}


.krzyzyk {
  background-image: url("../assets/krzyzyk1.png");
  background-size: 40px 40px;
  background-repeat: no-repeat;
  height: 40px;
  width: 40px;
  position: absolute;
  visibility: hidden;
  z-index: 1;
}

.krzyzyk1 {
  top: 310px;
  left: 135px;
  visibility: visible;
}

.krzyzyk2 {
  top: 390px;
  left: 135px;
  visibility: visible;
}

.odpowiedz {
  color: rgb(29, 56, 80);
  font-size: 30px;
  font-style: bold;
  font-weight: 700;
  font-family: "Proxima Nova", sans-serif;
  position: absolute;

}

.odpowiedz1 {
  top: 280px;
  left: 200px;
}

.odpowiedz2 {
  top: 360px;
  left: 200px;
}

.button-dalej {
  background-image: url("../assets/sprawdź_odpwowiedz_button1.png");
  background-size: 280px 65px;
  background-repeat: no-repeat;
  top: 490px;
  left: 200px;
  height: 67px;
  width: 280px;
  position: absolute;
  z-index: 2;
}

.button-dalej:hover {
  cursor: pointer;
}

.button-dalej:focus {
  /* border: 4px solid #08e926; */
  outline: thick double #08e926 !important;
}

.plansza-dobrze {
  background-image: url("../assets/KOMUNIKAT_dobra_odp.png");
  background-size: 862px 380px;
  background-repeat: no-repeat;
  height: 380px;
  width: 862px;
  position: absolute;
  left: 43px;
  top: 170px;
}

.plansza-zle {
  background-image: url("../assets/KOMUNIKAT_zla_odp.png");
  background-size: 862px 380px;
  background-repeat: no-repeat;
  height: 380px;
  width: 862px;
  position: absolute;
  left: 43px;
  top: 170px;
}

.button-dalej-dobrze {
  background-image: url("../assets/przycisk_dalej_imie.png");
  background-size: 154px 65px;
  background-position: -1px -5px;
  background-repeat: no-repeat;
  top: 430px;
  left: 370px;
  height: 58px;
  width: 154px;
  position: absolute;
  z-index: 2;
}

.button-dalej-dobrze:hover {
  cursor: pointer;
}

.button-dalej-dobrze:focus {
  /* border: 4px solid #08e926; */
  outline: thick double #08e926 !important;
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