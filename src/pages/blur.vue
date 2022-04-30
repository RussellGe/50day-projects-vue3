<script setup lang="ts">
import type { StyleValue } from 'vue'

const load = ref(0)

const blurring = () => {
  load.value++
  if (load.value > 99) {
    clearInterval(int)
  }
}

const int = setInterval(blurring, 30)

const getStyle = computed((): StyleValue => {
  return {
    filter: `blur(${scale(load.value, 0, 100, 30, 0)}px)`
  }
})

const getTextStyle = computed((): StyleValue => {
  return {
    opacity: load.value / 100
  }
})
const scale = (num: number, in_min: number, in_max: number, out_min: number, out_max: number) => {
  return ((num - in_min) * (out_max - out_min)) / (in_max - in_min) + out_min
}
</script>
<template>
  <section :style="getStyle" class="bg"></section>
  <div :style="getTextStyle" class="loading-text">{{ load }}%</div>
</template>
<style lang="less" scoped>
body {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
.bg {
  overflow: hidden;
  background: url('https://images.unsplash.com/photo-1576161787924-01bb08dad4a4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2104&q=80')
    no-repeat center center/cover;
  position: absolute;
  top: -30px;
  left: -30px;
  width: calc(100vw + 60px);
  height: calc(100vh + 60px);
  z-index: -1;
}

.loading-text {
  font-size: 50px;
  color: #fff;
}
</style>
