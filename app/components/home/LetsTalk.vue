<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const chartRef = ref(null)
const scrollProgress = ref(0)

const updateScrollProgress = () => {
  if (!chartRef.value) return

  const element = chartRef.value
  const rect = element.getBoundingClientRect()
  const windowHeight = window.innerHeight

  // Calculate when element enters and exits viewport
  const elementTop = rect.top
  const elementHeight = rect.height

  // Start animation when element is at bottom of viewport
  // Complete when element is at 70% of viewport height (30% from bottom)
  const scrollStart = windowHeight
  const scrollEnd = windowHeight * 0.5 // 50% from top

  const scrollRange = scrollStart - scrollEnd
  const currentScroll = scrollStart - elementTop

  // Calculate progress (0 to 1)
  const progress = Math.max(0, Math.min(1, currentScroll / scrollRange))

  scrollProgress.value = progress
}

onMounted(() => {
  window.addEventListener('scroll', updateScrollProgress)
  updateScrollProgress() // Initial calculation
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateScrollProgress)
})

// Compute transform based on scroll progress
const chartTransform = computed(() => {
  const y = 250 * (1 - scrollProgress.value)
  const opacity = scrollProgress.value
  return {
    transform: `translateY(${y}px)`,
    opacity: opacity
  }
})
</script>

<template>
  <section class="relative">
    <UContainer class="mx-auto lg:px-24 bg-[#004D42] overflow-hidden rounded-[30px]">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Left Content -->
        <div class="space-y-8 py-20 lg:py-32">
          <h2 class="text-4xl lg:text-[48px] font-extrabold text-white leading-tight lg:leading-[70px]">
            We are building<br>
            financial foundations
          </h2>

          <button
            class="inline-flex items-center gap-3 px-8 py-4 bg-[#B2EDA1] hover:bg-[#A0DC8F] text-[#111111] font-bold text-base rounded-full transition-colors leading-[30px]"
          >
            <span>Let's Talk</span>
            <svg
              width="16"
              height="16"
              viewBox="0 0 16 16"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M6 12L10 8L6 4"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </button>
        </div>

        <!-- Right Chart Graphic -->
        <div class="h-full flex items-end justify-end">
          <svg
            ref="chartRef"
            :style="chartTransform"
            class="w-full max-w-[372px] h-auto transition-all duration-0"
            viewBox="0 0 372 250"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <!-- Bar chart columns (colored) -->
            <path
              d="M137.134 105.312H120.811V137.65H137.134V105.312Z"
              fill="#22675D"
            />
            <path
              d="M165.62 86.6959H149.297V137.65H165.62V86.6959Z"
              fill="#30766C"
            />
            <path
              d="M194.105 66.1309H177.781V137.65H194.105V66.1309Z"
              fill="#3A8A7F"
            />
            <path
              d="M222.591 45.1879H206.268V137.65H222.591V45.1879Z"
              fill="#6CA88B"
            />
            <path
              d="M251.077 23.8549H234.754V137.65H251.077V23.8549Z"
              fill="#44C486"
            />

            <!-- Triangles on top of bars (colored) -->
            <path
              d="M127.919 87.8536L108.764 114.609H147.085L127.919 87.8536Z"
              fill="#22675D"
            />
            <path
              d="M157.596 65.168L138.43 91.9115H176.751L157.596 65.168Z"
              fill="#30766C"
            />
            <path
              d="M185.52 43.0557L166.365 69.7992H204.687L185.52 43.0557Z"
              fill="#3A8A7F"
            />
            <path
              d="M214.419 22.1124L195.264 48.856H233.585L214.419 22.1124Z"
              fill="#6CA88B"
            />
            <path
              d="M242.536 0L223.381 26.7435H261.702L242.536 0Z"
              fill="#44C486"
            />

            <!-- Reflections (white overlays) -->
            <path
              d="M120.81 137.65L15.7733 235.304L0 249.943L46.5404 250L58.3819 235.35L137.134 137.65H120.81Z"
              fill="white"
            />
            <path
              d="M149.295 137.65L90.2023 235.304L81.3184 249.943L127.882 250L132.822 235.35L165.618 137.65H149.295Z"
              fill="white"
            />
            <path
              d="M177.781 137.65L164.622 235.304L162.627 249.943L209.225 250L207.276 235.35L194.105 137.65H177.781Z"
              fill="white"
            />
            <path
              d="M206.268 137.65L239.052 235.304L243.947 249.943L290.579 250L281.73 235.35L222.591 137.65H206.268Z"
              fill="white"
            />
            <path
              d="M234.754 137.65L313.471 235.304L325.267 249.943L371.922 250L356.172 235.35L251.077 137.65H234.754Z"
              fill="white"
            />
          </svg>
        </div>
      </div>
    </UContainer>
  </section>
</template>
