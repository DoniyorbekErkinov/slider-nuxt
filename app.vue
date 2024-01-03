<script setup>
import { ref } from 'vue'
const data = ref(['/img/img_1.jpg', '/img/img_2.jpg', '/img/img_3.jpg', '/img/img_4.jpg', '/img/img_5.jpg'])
const currentImg = ref(0)
function changeImg(direction) {
  if (direction == 'left') {
    if (currentImg.value == 0) {
      currentImg.value = data.value.length - 1
    } else {
      currentImg.value -= 1
     }
  } else {
    if (currentImg.value == data.value.length - 1) {
      currentImg.value = 0
    } else {
      currentImg.value += 1
    }
  }
}
</script>
<template>
  <div class="w-screen h-screen bg-orange-50 flex justify-center items-center">
    <div class="border border-orange-100 rounded-2xl w-1/2 h-2/3 shadow-lg flex justify-between p-8">
      <div class="h-full w-[10%] ">
        <div class="w-full h-full border border-slate-400 rounded-xl flex flex-col justify-between overflow-hidden">
          <div :class="currentImg == i ? 'border border-orange-500 rounded-xl p-2' : ''" class="w-full h-1/5" v-for="(img, i) in data" :key="i">
            <img @click="currentImg = i" class="h-full w-full rounded-xl" :src="img"/>
          </div>
        </div>
      </div>
      <div class="w-[88%] h-full px-4 relative">
        <div class="w-full h-full flex justify-center items-center">
          <img class="w-full h-full rounded-xl" :src="data[currentImg]"/>
        </div>
        <div class="absolute w-10 h-10 bg-red-700 top-[50%] -left-1 rounded-full" @click="changeImg('left')"></div>
        <div class="absolute w-10 h-10 bg-red-700 top-[50%] -right-1 rounded-full" @click="changeImg('right')"></div>
      </div>
    </div>
  </div>
</template>
<style scoped>
body {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
</style>