<script setup lang="ts">
const currentSlide = ref(0)
const progress = ref(0)

// Carousel ref to access Embla API
const carouselRef = useTemplateRef('carouselRef')

const testimonials = [
  {
    image: '/images/finance-index/bohemian-man.png',
    quote: 'I must explain to you how all this mistaken. Tdea of denouncing pleasure and praising pain was born and I will give you a complete account. 😍',
    name: 'Roe Smith',
    title: 'Director, Growth Marketing',
    brand: '/images/brands/1.png'
  },
  {
    image: '/images/finance-index/quote-img2.png',
    quote: 'We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pleasure rationally encounter consequences that are pleasure rationally encounter ❤️ ❤️',
    name: 'Aurthoe De,',
    title: 'CEO - Dorid Co',
    brand: '/images/brands/2.png'
  },
  {
    image: '/images/finance-index/quote-img3.png',
    quote: 'Making this the first true 😍 generator on the Internet. It uses a dictionary of over words, combined with a handful of model sentence structures, to generate 👏👏',
    name: 'Dennis Lail',
    title: 'Marketer',
    brand: '/images/brands/3.png'
  },
  {
    image: '/images/finance-index/quote-img4.png',
    quote: 'Very denounce with righteous indignation and dislike men who are so beguiled and demoralized by the charms of pleasure of the moment, combined with a handfulso blinded by desire encounter 🥰 🤜 🤛',
    name: 'Peter Leo,',
    title: 'CTO - Criston',
    brand: '/images/brands/4.png'
  },
  {
    image: '/images/finance-index/quote-img5.png',
    quote: 'Making this the first true 😍 generator on the Internet. It uses a dictionary of over words, combined with a handful of model sentence structures, to generate 👏👏',
    name: 'Dennis Lail',
    title: 'Marketer',
    brand: '/images/brands/6.png'
  }
]

// Handle brand logo click - use Embla API to scroll to specific slide
const goToSlide = (index: number) => {
  if (carouselRef.value?.emblaApi) {
    carouselRef.value.emblaApi.scrollTo(index)
  }
}

// Animate progress bar synced with slide changes
let progressAnimationFrame: number | null = null
const startProgress = () => {
  const startTime = Date.now()
  // Slightly less than autoplay delay to account for transition time
  const duration = 11500 // ~11.5 seconds (12s autoplay - transition time)

  if (progressAnimationFrame) {
    cancelAnimationFrame(progressAnimationFrame)
  }

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

// Subscribe to Embla select event and update currentSlide
const onCarouselInit = () => {
  if (!carouselRef.value?.emblaApi) return

  const emblaApi = carouselRef.value.emblaApi

  // Subscribe to 'select' event - fires when slide changes
  emblaApi.on('select', () => {
    currentSlide.value = emblaApi.selectedScrollSnap()
    startProgress() // Restart progress on every slide change
  })

  // Set initial slide and start progress
  currentSlide.value = emblaApi.selectedScrollSnap()
  startProgress()
}

// Watch for carousel ref to be ready
watch(() => carouselRef.value?.emblaApi, (api) => {
  if (api) {
    onCarouselInit()
  }
})

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
  <section class="py-[120px] max-md:py-20 bg-[#ECF1F1]">
    <UContainer class="max-md:px-4">
      <div class="relative bg-white shadow-[0px_5px_10px_rgba(0,0,0,0.05)] rounded-[30px] overflow-hidden">
        <!-- Background Images -->
        <div class="absolute left-[9%] bottom-[117px] pointer-events-none z-0">
          <NuxtImg
            src="/images/finance-index/customers-quote-bg.svg"
            alt="background"
            class="w-full h-full"
          />
        </div>
        <!-- Decorative image left side -->
        <div class="absolute left-0 top-12 z-0 pointer-events-none">
          <NuxtImg
            src="/images/finance-index/card-quote-img.png"
            alt="decoration"
          />
        </div>

        <!-- Quote Icon -->
        <div class="absolute top-[18%] right-[46%] z-10 max-md:hidden">
          <NuxtImg
            src="/images/finance-index/quote.svg"
            alt="quote icon"
            class="w-auto h-auto"
          />
        </div>

        <!-- Carousel Content -->
        <div class="relative z-2">
          <UCarousel
            ref="carouselRef"
            :items="testimonials"
            :ui="{
              item: 'w-full',
              container: 'gap-0'
            }"
            :loop="true"
            :autoplay="{ delay: 12000 }"
            :arrows="false"
            :indicators="false"
          >
            <template #default="{ item }">
              <div class="pt-[100px] pb-[49px] pr-[50px] max-md:pt-16 max-md:pb-8 max-md:pr-4 max-md:pl-4">
                <div class="grid md:grid-cols-2 gap-8 items-end">
                  <!-- Left: Image -->
                  <div class="min-h-[298px] max-w-[320px] w-full mx-auto flex items-end justify-center relative">
                    <span class="relative z-2">
                      <NuxtImg
                        :src="item.image"
                        :alt="item.name"
                        class="w-full h-fulll max-w-full"
                      />
                    </span>
                  </div>

                  <!-- Right: Quote Text -->
                  <div class="max-w-[520px] w-full h-full flex items-start justify-end flex-col">
                    <p class="font-['DM_Sans'] text-lg font-medium leading-9 text-[#111111] mb-[27px] line-clamp-3">
                      {{ item.quote }}
                    </p>
                    <div class="font-['DM_Sans'] text-[#111111]">
                      <span class="block text-lg font-bold leading-[30px]">
                        {{ item.name }}
                      </span>
                      <span class="block">
                        {{ item.title }}
                      </span>
                    </div>
                  </div>
                </div>
              </div>
            </template>
          </UCarousel>
        </div>

        <!-- Footer with Brand Logos -->
        <div class="relative border-t border-black/10 py-5 px-[38px] max-md:px-4 w-full">
          <!-- Animated Progress Line -->
          <div
            class="absolute top-[-2px] left-0 h-[2px] bg-[#44C486] transition-none"
            :style="{ width: `${progress}%` }"
          />

          <!-- Brand Logo Navigation -->
          <div class="flex items-center justify-evenly gap-5 flex-wrap w-full">
            <button
              v-for="(testimonial, index) in testimonials"
              :key="index"
              class="cursor-pointer transition-opacity hover:opacity-100"
              :class="index === currentSlide ? 'opacity-100' : 'opacity-60'"
              @click="goToSlide(index)"
            >
              <NuxtImg
                :src="testimonial.brand"
                alt="brand logo"
                class="mx-auto h-6.5 w-auto"
              />
            </button>
          </div>
        </div>
      </div>
    </UContainer>
  </section>
</template>
