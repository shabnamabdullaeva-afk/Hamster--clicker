<script setup lang="ts">
import { ref } from 'vue';
import TshirtComponent from './components/TshirtComponent.vue';
import CapComponent from './components/CapComponent.vue';
import SodaComponent from './components/SodaComponent.vue';
import CigaretteComponent from './components/CigaretteComponent.vue';

// null, undefined
// string -   'asdasd'   "asdfasdf asdf123"
// number -    12312312  123.123123123
// boolean -   true false


// && - оба условия должны выполниться
// || - одно условие должно выполниться

const clicks = ref(0)

const scale = ref(1)


const TShirtValue = ref<Boolean>(false)
const CapValue = ref<Boolean>(false)
const SodaValue = ref<Boolean>(false)
const CigaretteValue = ref<Boolean>(false)

function EnableShirt() {
  if (clicks.value >= 25) {
    TShirtValue.value = true
    clicks.value -= 25
  }
}
function EnableCap() {
  if (clicks.value >= 15) {
    CapValue.value = true
    clicks.value -= 15
  }
}
function EnableSoda() {
  if (clicks.value >= 10) {
    SodaValue.value = true
    clicks.value -= 10
  }
}
function EnableCigarette() {
  if (clicks.value >= 5) {
    CigaretteValue.value = true
    clicks.value -= 5
  }
}

const clicked = ref(false)

const buttons = [
  {
    title: "T-Shirt",
    image: "https://cdn-icons-png.freepik.com/512/17901/17901534.png?ga=GA1.1.929282706.1756977649",
    function: EnableShirt,
    price: "25 денег"
  },
  {
    title: "Cap",
    image: "https://cdn-icons-png.freepik.com/512/7863/7863443.png?ga=GA1.1.929282706.1756977649",
    function: EnableCap,
    price: "15 денег"
  },
  {
    title: "Soda",
    image: "https://cdn-icons-png.freepik.com/512/13519/13519792.png?ga=GA1.1.929282706.1756977649",
    function: EnableSoda,
    price: "10 денег"
  },
  {
    title: "Cigarette",
    image: "https://cdn-icons-png.freepik.com/512/7853/7853974.png?ga=GA1.1.1988972297.1762586614",
    function: EnableCigarette,
    price: "5 денег"
  }
]

function returnScale() {
  scale.value = 1
  clicked.value = false
  // hamsterCurrent.value = 'https://img01.kupiprodai.ru/082020/1598209377643.jpeg'
}


function clickHamster() {
  clicks.value += 1
  scale.value = 1.02
  clicked.value = true
  // hamsterCurrent.value = './assets/HAMSTER_FUCK.png'
  setTimeout(returnScale, 50)
}



</script>

<template>
  <v-app>
    <div class="app">
      <div class="content">
        <h1 style="text-align: center;">
          hamster-clicker
        </h1>
        <h1 style="text-align: center"> {{ clicks }} </h1>
        <div style="justify-items: center;">
          <div @click="clickHamster">
            <img :style="'scale:' + scale" style="pointer-events: none;
          user-select: none;" src="./assets/HAMSTER_FUCK.png" v-if="clicked"></img>
          </div>
          <div style="width: fit-content;" @click="clickHamster">
            <img :style="'scale:' + scale" style="pointer-events: none;
          user-select: none;" src='./assets/1598209377643.jpeg' @click="clickHamster" v-if="!clicked"></img>
          </div>
          <TshirtComponent v-if="TShirtValue"/>
          <CapComponent v-if="CapValue"/>
          <SodaComponent v-if="SodaValue"/>
          <CigaretteComponent v-if="CigaretteValue"/>
        </div>
        <v-container style="justify-content: center; 
      display: flex;">
          <div class="card" v-for="b in buttons" @click="b.function">
            <p class="card-text">{{ b.title }}</p>
            <div class="hight">
              <img class="img-card" :src="b.image">
            </div>
            <div>
              <p class="card-text">{{ b.price }}</p>
            </div>
          </div>
        </v-container>
      </div>
    </div>
  </v-app>
</template>

<style scoped>
.card {
  background-color: rgba(73, 181, 129, 0.164);
  width: 100px;
  height: 100px;
  border-style: solid;
  border-width: 3px;
  border-color: rgb(38, 126, 89);
  margin: px;
  box-sizing: border-box;
  justify-items: center;
  border-radius: 0.2cm;
}

.content {
  justify-self: center;
  background-color: rgba(114, 246, 204, 0.466);
  width: 50%;
  border-radius: 1cm;
  backdrop-filter: blur(15px);
}

.card-text {
  text-align: center;
  font-size: medium;
}

.img-card {
  width: 50px;

}

img {
  width: 300px;
}

img:active {
  scale: 1.05;
}

.hight {
  max-height: 50px;
}

button {
  color: rgb(255, 115, 0);
}

.app {
  background-image: url(assets/1123x630_0xSBuyDGlI_4326298622077527833.jpg);
  background-size: cover;
  min-height: 100vh;
}
</style>
