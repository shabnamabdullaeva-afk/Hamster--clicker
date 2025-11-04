<script setup lang="ts">
import { ref } from 'vue';


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

function EnableShirt(){
  if(clicks.value >= 25){
TShirtValue.value=true
clicks.value -= 25
}
}
function EnableCap(){
  if(clicks.value >= 15){
CapValue.value=true
clicks.value -= 15
}
}
function EnableSoda(){
  if(clicks.value >= 10){
SodaValue.value=true
clicks.value -= 10
}
}


const clicked = ref(false)

const buttons =  [
  {
    title:"T-Shirt",
    image: "https://cdn-icons-png.freepik.com/512/17901/17901534.png?ga=GA1.1.929282706.1756977649",
    function: EnableShirt,
    price:"25 денег"
  },
  {
    title:"Cap",
    image: "https://cdn-icons-png.freepik.com/512/7863/7863443.png?ga=GA1.1.929282706.1756977649",
    function: EnableCap,
    price:"15 денег"
  },
  {
    title:"soda",
     image: "https://cdn-icons-png.freepik.com/512/13519/13519792.png?ga=GA1.1.929282706.1756977649",
     function: EnableSoda,
     price:"10 денег"
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
        <img :style="'scale:' + scale"
          style="pointer-events: none;
          user-select: none;"
          src="./assets/HAMSTER_FUCK.png"
          v-if="clicked"
        ></img>
        </div>
        <div style="width: fit-content;" 
         @click="clickHamster">
        <img :style="'scale:' + scale"
          style="pointer-events: none;
          user-select: none;"
          src='./assets/1598209377643.jpeg'
          @click="clickHamster"
          v-if="!clicked"
        ></img>
        </div>
        <img src="./assets/acetone-20251023-173345-290.png"
        style="position: absolute; 
        left: 25%;
        top: 40%; 
        scale: 1;
        user-select: none;
        pointer-events: none;" 
        v-if="TShirtValue"/>
        <img src="./assets/acetone-20251023-17582-520.png"
        style="position: absolute; 
        left: 24.5%;
        top: -1.5%; 
        scale: 0.3;
        user-select: none;
        pointer-events: none;" 
        v-if="CapValue"/>
        <img src="./assets/pngtree-classic-glass-soda-bottle-png-image_15287878.png"
        style="position: absolute; 
        left: 25.5%;
        top: 18%; 
        scale: 0.3;
        rotate: -37deg;
        pointer-events: none;" 
        v-if="SodaValue"/>

      </div>
      <v-container 
      style="justify-content: center; 
      display: flex;">
        <div class="card"  v-for="b in buttons" @click="b.function">
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
  background-color: rgb(55, 124, 184);
  width: 100px;
  height: 100px;
  border-style: solid;
  border-width: 3px;
  border-color: rgb(47, 103, 153);
  margin: px;
  box-sizing: border-box;
  justify-items: center;
}
.content{
  justify-self: center;
  background-color: rgb(93, 179, 255);
  width: 50%;
}
.card-text{
  text-align: center;
  font-size: medium;
}
.img-card{
  width:50px;
  
}
img{
  width: 300px;
}

img:active {
scale: 1.05;
}
.hight{
  max-height: 50px;
}

button {
  color: rgb(255, 115, 0);
}
.app{
  background-image: url(assets/1123x630_0xSBuyDGlI_4326298622077527833.jpg);
  background-size: cover;
  min-height: 100vh;
}

</style>
