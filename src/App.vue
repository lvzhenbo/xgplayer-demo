<script setup lang="ts">
import Player from 'xgplayer'
import 'xgplayer/dist/index.min.css'
import HlsJsPlugin from 'xgplayer-hls.js'
import { onMounted, ref } from 'vue'

const player = ref<Player | null>(null)
const videoRef = ref<HTMLVideoElement | null>(null)

onMounted(() => {
  player.value = new Player({
    el: videoRef.value as HTMLElement,
    fluid: true,
    autoplay: true,
    url: 'https://events-delivery.apple.com/1505clvgxdwlbjrjhxtjdgcdxaiabvuf/m3u8/vod_index-LHDoZDhTrsKLsbrZKqYpbWraixsWQHkw.m3u8',
    plugins: [HlsJsPlugin]
  })
})

const handleChange = () => {
  if (!player.value) return
  player.value?.switchURL(
    'https://events-delivery.apple.com/0105cftwpxxsfrpdwklppzjhjocakrsk/m3u8/vod_index-PQsoJoECcKHTYzphNkXohHsQWACugmET.m3u8?74992'
  )
  player.value.currentTime = 1000 // 16:40
}
</script>

<template>
  <div style="width: 100%; height: 100%">
    <button @click="handleChange">切换视频</button>
    <div ref="videoRef" class="video-js"></div>
  </div>
</template>

<style scoped></style>
