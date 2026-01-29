<script setup>
const videoRef = ref(null)
const isPlaying = ref(false)

function togglePlay() {
  if (videoRef.value) {
    if (isPlaying.value) {
      videoRef.value.pause()
    } else {
      videoRef.value.play()
    }
  }
}

function handlePlay() {
  isPlaying.value = true
}

function handlePause() {
  isPlaying.value = false
}
</script>

<template>
  <div class="relative max-w-[470px] h-[340px] rounded-[30px] overflow-hidden z-2">
    <!-- Video -->
    <video
      ref="videoRef"
      class="w-full h-full object-cover"
      loop
      autoplay
      playsinline
      preload="auto"
      @play="handlePlay"
      @pause="handlePause"
    >
      <source
        src="https://staco-react.vercel.app/assets/h6-video-DaLtBHE1.mp4"
        type="video/mp4"
      >
      Your browser does not support the video tag.
    </video>

    <!-- Gradient Overlay -->
    <div
      class="absolute inset-0 pointer-events-none"
      style="background: linear-gradient(117.62deg, rgba(0, 0, 0, 0) 51.24%, rgba(0, 0, 0, 1) 100%)"
    />

    <!-- Play/Pause Button -->
    <button
      class="absolute bottom-[30px] right-[30px] w-[50px] h-[50px] bg-white rounded-full flex items-center justify-center hover:bg-gray-100 transition-colors z-10"
      :aria-label="isPlaying ? 'Pause video' : 'Play video'"
      @click="togglePlay"
    >
      <UIcon
        :name="isPlaying ? 'i-heroicons-pause' : 'i-heroicons-play'"
        class="w-7 h-7 text-[#44C486]"
      />
    </button>
  </div>
</template>
