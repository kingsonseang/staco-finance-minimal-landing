<script setup lang="ts">
const currentSlide = ref(0)
const progress = ref(0)

// Carousel ref to access Embla API
const carouselRef = useTemplateRef('carouselRef')

const slides = [
  {
    subtitle: 'Why Choose Us',
    title: 'Discover business Opportunities',
    description: 'We use as filler text for layouts, non-readability is of great importancebut because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.',
    features: [
      'Profile Consultation',
      'Asset management',
      'No-risk business idea'
    ],
    image: '/images/img/feature-team1.png'
  },
  {
    subtitle: 'Why Choose Us',
    title: 'Manage team increase productivity',
    description: 'We use as filler text for layouts, non-readability is of great importancebut because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.',
    features: [
      '99% Survey Report',
      'Trusted by teams',
      'Self-Service'
    ],
    image: '/images/img/feature-team2.png'
  },
  {
    subtitle: 'Why Choose Us',
    title: 'Manage team increase productivity',
    description: 'We use as filler text for layouts, non-readability is of great importancebut because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.',
    features: [
      '99% Survey Report',
      'Trusted by teams',
      'Self-Service'
    ],
    image: '/images/img/feature-team3.png'
  }
]

// Handle image click - use Embla API to scroll to specific slide
const goToSlide = (index: number) => {
  if (carouselRef.value?.emblaApi) {
    carouselRef.value.emblaApi.scrollTo(index)
  }
}

// Subscribe to Embla select event and update currentSlide
const onCarouselInit = () => {
  if (!carouselRef.value?.emblaApi) return

  const emblaApi = carouselRef.value.emblaApi

  // Subscribe to 'select' event - fires when slide changes
  emblaApi.on('select', () => {
    currentSlide.value = emblaApi.selectedScrollSnap()
    // Reset progress when slide changes
    progress.value = 0
  })

  // Set initial slide
  currentSlide.value = emblaApi.selectedScrollSnap()
}

// Watch for carousel ref to be ready
watch(() => carouselRef.value?.emblaApi, (api) => {
  if (api) {
    onCarouselInit()
  }
})

// Simulate progress bar that fills up over the autoplay duration
// This is a visual indicator, actual slide change is controlled by UCarousel's autoplay
let progressAnimationFrame: number | null = null
const animateProgress = () => {
  const startTime = Date.now()
  const duration = 6400 // Match carousel autoplay duration

  const updateProgress = () => {
    const elapsed = Date.now() - startTime
    const newProgress = Math.min((elapsed / duration) * 100, 100)
    progress.value = newProgress

    if (newProgress < 100) {
      progressAnimationFrame = requestAnimationFrame(updateProgress)
    }
  }

  updateProgress()
}

// Watch currentSlide to restart progress animation
watch(currentSlide, () => {
  if (progressAnimationFrame) {
    cancelAnimationFrame(progressAnimationFrame)
  }
  animateProgress()
}, { immediate: true })

onUnmounted(() => {
  if (progressAnimationFrame) {
    cancelAnimationFrame(progressAnimationFrame)
  }

  // Cleanup Embla event listeners
  if (carouselRef.value?.emblaApi) {
    carouselRef.value.emblaApi.off('select', () => {})
  }
})
</script>

<template>
  <section class="py-[120px] bg-white">
    <UContainer>
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Left: Content Carousel -->
        <div>
          <UCarousel
            ref="carouselRef"
            :items="slides"
            :ui="{
              item: 'w-full',
              container: 'gap-0'
            }"
            :loop="true"
            :autoplay="{ delay: 6400 }"
            :arrows="false"
            :indicators="false"
          >
            <template #default="{ item }">
              <div class="space-y-6">
                <!-- Subtitle -->
                <span class="inline-block text-[#44C486] font-['DM_Sans'] text-lg font-bold leading-[30px] tracking-[0.2em]">
                  {{ item.subtitle }}
                </span>

                <!-- Title -->
                <h2 class="font-['Montserrat_Alternates'] font-bold text-[40px] leading-[60px] text-[#111111] mb-10">
                  {{ item.title }}
                </h2>

                <!-- Description -->
                <p class="text-base leading-relaxed text-gray-700">
                  {{ item.description }}
                </p>

                <!-- Features List -->
                <ul class="flex items-center gap-5 justify-between flex-wrap max-w-[354px] list-none mt-[30px]">
                  <li
                    v-for="(feature, index) in item.features"
                    :key="index"
                    class="flex items-center gap-[10px] font-medium text-[15px] leading-[26px] text-[#111111]"
                  >
                    <UIcon
                      name="i-heroicons-check"
                      class="w-[18px] h-[18px] text-[#0EC36B]"
                    />
                    <span>{{ feature }}</span>
                  </li>
                </ul>
              </div>
            </template>
          </UCarousel>
        </div>

        <!-- Right: Image Slider -->
        <div class="flex items-center justify-start gap-5">
          <div
            v-for="(slide, index) in slides"
            :key="index"
            class="relative cursor-pointer rounded-[20px] overflow-hidden transition-all duration-300"
            :class="{
              'w-[17.54%] h-[460px]': index !== currentSlide,
              'w-[57.89%] h-[460px]': index === currentSlide
            }"
            @click="goToSlide(index)"
          >
            <!-- Image -->
            <NuxtImg
              :src="slide.image"
              :alt="`Feature ${index + 1}`"
              class="w-full h-full object-cover object-center transition-transform duration-300"
            />

            <!-- Dark overlay gradient (always shown on inactive) -->
            <div
              v-if="index !== currentSlide"
              class="absolute inset-0 bg-gradient-to-b from-black/10 to-black/70 transition-opacity duration-300"
            />

            <!-- Arrow icon (only on inactive) -->
            <div
              v-if="index !== currentSlide"
              class="absolute bottom-[30px] left-1/2 -translate-x-1/2 transition-opacity duration-300"
            >
              <NuxtImg
                src="/images/icons/arrow-right-white.svg"
                alt="arrow"
                class="w-6 h-6"
              />
            </div>

            <!-- Progress bar (only on active) -->
            <div
              v-if="index === currentSlide"
              class="absolute bottom-[30px] left-5 right-5 h-2 bg-white/20 rounded overflow-hidden"
            >
              <div
                class="h-full bg-white/50 transition-none"
                :style="{ width: `${progress}%` }"
              />
            </div>
          </div>
        </div>
      </div>
    </UContainer>
  </section>
</template>
