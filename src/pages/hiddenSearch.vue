<script setup lang="ts">
const show = ref(false)
const el = ref<HTMLInputElement>()
const showInput = () => {
  show.value = !show.value
  if (show.value) {
    el.value?.focus()
  }
}
</script>
<template>
  <div class="search-wrapper">
    <input
      ref="el"
      class="search-input"
      :class="!show ? 'hide' : ''"
      type="text"
      placeholder="search..."
    />
    <div class="search-icon" @click="showInput">
      <div class="i-carbon-search"></div>
    </div>
  </div>
</template>
<style lang="less" scoped>
.search-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 800px;
  width: 100%;
  background: turquoise;
  .search-input {
    height: 40px;
    box-sizing: border-box;
    padding: 10px;
    outline: none;
    width: 200px;
    transition: width 0.3s ease;
  }
  .hide {
    width: 0;
    padding: 5px 0;
  }
  .search-icon {
    font-size: 20px;
    height: 40px;
    width: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #fff;
  }
}
</style>
