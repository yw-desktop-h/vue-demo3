<template>
  <div class="home">
    <div>count:{{count}}</div>
    <div>doubleCount:{{doubleCount}}</div>
    <div class="content" :class="tr?'tr':''" @click="onClick"></div>
    <div>
      <span>products:</span>
      <List :list="list"></List>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue'
import {storeToRefs} from 'pinia'
import {useCounterStore } from '@/store/count.js'

import List from '@/components/list.vue'

const counterStore=useCounterStore();
const {count,name,doubleCount }=storeToRefs(counterStore);
const {increment}=counterStore;
setTimeout(() => {
  increment()
}, 3000);
const tr=ref(false);
const onClick=function(){
  tr.value=!tr.value
}

const list=[
  {url:require('@/assets/imgs/img1.webp'),title:'product1',desc:'水果'},
  {url:require('@/assets/imgs/img2.webp'),title:'product2',desc:'水果'},
  {url:require('@/assets/imgs/img3.jpg'),title:'product3',desc:'水果'},
  {url:require('@/assets/imgs/img4.jpg'),title:'product4',desc:'水果'},
  {url:require('@/assets/imgs/img5.webp'),title:'product5',desc:'水果'},
]

</script>
<style scoped>
.content{
  width: 100px;
  height: 100px;
  background-color: red;
  transform: translateX(0);
}
.tr{
  transform: translateX(100px);
  transition: transform 3s linear 0s;
}

</style>
