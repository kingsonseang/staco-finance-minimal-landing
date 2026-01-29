<script setup lang="ts">
const props = defineProps({
  words: {
    type: Array as () => string[],
    required: true
  }
})

const currentIndex = ref(0)
const progress = ref(0)
const wordRefs = ref<HTMLElement[]>([])
const maxWidth = ref(0)

const WORD_DURATION = 3000 // 3 seconds per word
const ANIMATION_INTERVAL = 30 // Update every 30ms for smooth animation

// Get the maximum width from all words
const updateMaxWidth = () => {
  const widths = wordRefs.value.map(el => el?.offsetWidth || 0)
  maxWidth.value = Math.max(...widths)
}

// Cycle through words
const cycleWord = () => {
  currentIndex.value = (currentIndex.value + 1) % props.words.length
  progress.value = 0 // Reset progress when changing words
}

onMounted(() => {
  // Measure max width after mount
  nextTick(() => {
    updateMaxWidth()
  })

  // Progress animation - fills from 0 to 100% over WORD_DURATION
  const progressInterval = setInterval(() => {
    progress.value += (100 / (WORD_DURATION / ANIMATION_INTERVAL))

    if (progress.value >= 100) {
      cycleWord()
    }
  }, ANIMATION_INTERVAL)

  onBeforeUnmount(() => {
    clearInterval(progressInterval)
  })
})
</script>

<template>
  <span class="text-[#b2eda1] inline-block align-top -mt-[11px] ml-[10px] py-[0.2em] relative text-left">
    <span class="relative inline-block">
      <!-- Words stack -->
      <b
        v-for="(word, index) in words"
        :key="index"
        :ref="(el) => { if (el) wordRefs[index] = el as HTMLElement }"
        class="inline-block text-nowrap transition-opacity duration-500"
        :class="{
          'opacity-100 relative after:absolute after:bottom-0 after:left-0 after:h-2 after:bg-[#b2eda1] after:transition-none after:w-(--loader-width)': index === currentIndex,
          'opacity-0 absolute top-0 left-0 pointer-events-none': index !== currentIndex
        }"
        :style="{
          '--loader-width': `${progress}%`
        }"
      >
        {{ word }}
      </b>
    </span>
  </span>
</template>
