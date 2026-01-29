<script setup lang="ts">
const props = defineProps({
  words: {
    type: Array as () => string[],
    required: true
  }
})

const currentIndex = ref(0)
const underlineWidth = ref(0)
const wordRefs = ref<HTMLElement[]>([])

const WORD_DURATION = 3000 // 3 seconds per word

// Update underline width based on current word
const updateUnderlineWidth = () => {
  const currentWordElement = wordRefs.value[currentIndex.value]
  if (currentWordElement) {
    underlineWidth.value = currentWordElement.offsetWidth
  }
}

// Cycle through words
const cycleWord = () => {
  currentIndex.value = (currentIndex.value + 1) % props.words.length

  // Wait for DOM update before measuring width
  nextTick(() => {
    updateUnderlineWidth()
  })
}

onMounted(() => {
  // Initial width measurement
  updateUnderlineWidth()

  // Set up word cycling interval
  const cycleInterval = setInterval(cycleWord, WORD_DURATION)

  onBeforeUnmount(() => {
    clearInterval(cycleInterval)
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
          'opacity-100 relative': index === currentIndex,
          'opacity-0 absolute top-0 left-0 pointer-events-none': index !== currentIndex
        }"
      >
        {{ word }}
      </b>

      <!-- Animated underline -->
      <span
        class="absolute bottom-0 left-0 h-2 bg-[#b2eda1] transition-all duration-500 ease-in-out"
        :style="{ width: `${underlineWidth}px` }"
      />
    </span>
  </span>
</template>
