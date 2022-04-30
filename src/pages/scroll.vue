<script setup lang="ts">
const els = ref<HTMLElement[]>([])
const el = (ele: HTMLElement) => {
  els.value?.push(ele)
}
function checkBoxes() {
  const triggerBottom = (window.innerHeight / 5) * 4

  els.value.forEach((box) => {
    const boxTop = box.getBoundingClientRect().top

    if (boxTop < triggerBottom) {
      box.classList.add('show')
    } else {
      box.classList.remove('show')
    }
  })
}
window.addEventListener('scroll', checkBoxes)
onMounted(() => {
  checkBoxes()
})
</script>
<template>
  <div class="container-box">
    <h1>Scroll to see the animation</h1>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
    <div :ref="el" class="box"><h2>Content</h2></div>
  </div>
</template>

<style lang="less" scoped>
.container-box {
  background-color: #efedd6;
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0;
  overflow-x: hidden;
  h1 {
    margin: 10px;
  }

  .box {
    background-color: steelblue;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 400px;
    height: 200px;
    margin: 10px;
    border-radius: 10px;
    box-shadow: 2px 4px 5px rgba(0, 0, 0, 0.3);
    transform: translateX(400%);
    transition: transform 0.4s ease;
  }
  .box:nth-of-type(even) {
    transform: translateX(-400%);
  }

  .box.show {
    transform: translateX(0);
  }

  .box h2 {
    font-size: 45px;
  }
}
</style>
