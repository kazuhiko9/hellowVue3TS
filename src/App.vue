<script setup lang="ts">
import Stone from './components/Stone.vue'
import {ref} from 'vue'
const lastXY = 8
const moves = [
              {x:1,y:0},    // 右
              {x:1,y:1},    // 右下
              {x:0,y:1},    // 下
              {x:-1,y:1},   // 左下
              {x:-1,y:0},   // 左
              {x:-1,y:-1},  // 左上
              {x:0,y:-1},   // 上
             ]
let myStone = ref(1);
let stones: any = ref([[]])

window.onload = ()=>{
  init()
}

const init = () => {
  for (let y = 0; y < lastXY; y++) {
    stones.value[y] = [0,0,0,0,0,0,0,0]
  }
  stones.value[3][3] = 1
  stones.value[4][4] = 1
  stones.value[3][4] = -1
  stones.value[4][3] = -1
}

const setStone = (y:number, x:number) => {
  if (stones.value[y][x] != 0) return

  stones.value[y][x] = myStone.value
  myStone.value = myStone.value * -1
}

const searchStone = (y:number, x:number) => {
  let reverse:number = 0
  for (const move in moves) {
    reverse = reverse + searchStoneLine(y,x,move)
  }
  return reverse
}

const searchStoneLine = (y:number, x:number, move:any) => {
  let reverse:number = 0
  for (const move in moves) {
  }
  return reverse
}

</script>
<template>
  <button @click="init()">Reset</button>
  手番:{{myStone}}
  <table>
    <tr v-for="(stoneLine, y) in stones" :key="y">
      <td v-for="(stone, x) in stoneLine" :key="x">
        <button @click="setStone(y,x)" style="width: 25px;"><Stone :stone="stone"/></button>
      </td>
    </tr>
  </table>
</template>