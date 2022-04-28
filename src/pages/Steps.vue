<script setup lang="ts">
import type { StyleValue } from 'vue'

const current = ref(1)
const getStyle = computed((): StyleValue => {
  return {
    width: `${(current.value * 370 - 370) / 3}px`
  }
})
const change = (val: number) => {
  if ((val === 1 && current.value !== 4) || (val === -1 && current.value !== 1))
    current.value += val
}
</script>
<template>
  <div flex items-center width-100>
    <div class="container">
      <div class="circle-container">
        <div class="progress" :style="getStyle"></div>
        <div class="progress-under"></div>
        <div
          class="circle"
          :class="[current >= i ? 'active' : '']"
          v-for="i in 4"
          :key="i"
        >
          {{ i }}
        </div>
      </div>
      <div class="button-container">
        <div
          class="btn"
          @click="change(-1)"
          :class="[current === 1 ? 'disable' : '']"
        >
          prev
        </div>
        <div
          class="btn"
          @click="change(1)"
          :class="[current === 4 ? 'disable' : '']"
        >
          next
        </div>
      </div>
    </div>
  </div>
</template>
ƒ
<style lang="less" scoped>
.container {
  width: 90vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  flex-direction: column;
  .circle-container {
    display: flex;
    position: relative;
    align-items: center;
    margin-bottom: 60px;
    .progress {
      background: tomato;
      height: 10px;
      z-index: -1;
      position: absolute;
      transition: 0.5s ease-in-out;
    }
    .progress-under {
      background: gray;
      height: 10px;
      width: 370px;
      z-index: -2;
      position: absolute;
    }
    .circle {
      background: #fff;
      height: 40px;
      width: 40px;
      border: 10px gray solid;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      margin-right: 70px;
    }
    .active {
      transition-delay: .45s;
      border-color: tomato;
    }
    .circle:last-child {
      margin-right: 0;
    }
  }
  .button-container {
    display: flex;
    width: 230px;
    justify-content: space-around;
    .disable {
      background: gray;
      cursor: not-allowed;
    }
  }
}
</style>
