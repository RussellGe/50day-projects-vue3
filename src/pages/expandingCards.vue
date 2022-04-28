<script setup lang="ts">
import type { StyleValue } from 'vue'
import { cardInfos } from '../config/expandingCards'

const getStyle = (url: string): StyleValue => {
  return {
    backgroundImage: `url(${url})`
  }
}

const currentImg = ref(cardInfos[0].url)

const changeCurrentUrl = (url: string) => {
  currentImg.value = url
}
</script>
<template>
  <div flex width-100>
    <div
      class="panel"
      :class="[item.url === currentImg ? 'active' : '']"
      @click="changeCurrentUrl(item.url)"
      v-for="item in cardInfos"
      :key="item.url"
      :style="getStyle(item.url)"
    >
      <h3>{{ item.desc }}</h3>
    </div>
  </div>
</template>
ƒ
<style lang="less" scoped>
.panel {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 80vh;
  border-radius: 50px;
  color: #fff;
  cursor: pointer;
  flex: 0.5;
  margin: 10px;
  position: relative;
  -webkit-transition: all 700ms ease-in;
  h3 {
    font-size: 24px;
    position: absolute;
    bottom: 20px;
    left: 20px;
    margin: 0;
    opacity: 0;
  }
}
.active {
  flex: 5;
  h3 {
    opacity: 1;
    transition: opacity 0.3s ease-in 0.4s;
  }
}
</style>
