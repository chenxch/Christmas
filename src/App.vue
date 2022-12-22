<script setup lang="ts">
import { onMounted, ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
// import 'sakana'
import './sakana.scss'
import Sakana from './sakana.js'
const play = ref(false)
const audioRef = ref<HTMLAudioElement | null>(null)
onMounted(() => {
  Sakana.init({
  el:         '.sakana-box',     // 启动元素 node 或 选择器
  scale:      1,                // 缩放倍数
  canSwitchCharacter: false,      // 允许换角色
});
const html = document.querySelector('html')!
html.addEventListener('click', () => {
  if (audioRef.value) {
    if (!play.value) {
      audioRef.value.play()
      play.value = true
    }
  }
})
})


</script>

<template>
  <div class="snow-container">
    <div class="snow foreground"></div>
    <div class="snow foreground layered"></div>
    <div class="snow middleground"></div>
    <div class="snow middleground layered"></div>
    <div class="snow background"></div>
    <div class="snow background layered"></div>
  </div>
  <div class="sakana-box">
  </div>
  <audio ref="audioRef" loop>
    <source src="/music.mp3" type="audio/mpeg">
  </audio>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
