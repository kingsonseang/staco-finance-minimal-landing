<script setup>
import HeroVideo from './HeroVideo.vue'

const words = ['Easier', 'Faster', 'Smarter', 'Better']
const currentIndex = ref(0)
const progress = ref(0)

const currentWord = computed(() => words[currentIndex.value])

const WORD_DURATION = 3000 // 3 seconds per word
const ANIMATION_INTERVAL = 30 // Update every 30ms

onMounted(() => {
    // Progress animation
    const progressInterval = setInterval(() => {
        progress.value += (100 / (WORD_DURATION / ANIMATION_INTERVAL))

        if (progress.value >= 100) {
            progress.value = 0
            currentIndex.value = (currentIndex.value + 1) % words.length
        }
    }, ANIMATION_INTERVAL)

    onBeforeUnmount(() => {
        clearInterval(progressInterval)
    })
})
</script>

<template>
    <section class="relative bg-[#1F2334] min-h-[100svh] flex items-center overflow-hidden">
        <!-- Decorative SVG curves from Figma -->
        <div class="absolute inset-0 pointer-events-none overflow-hidden">
            <!-- Large curved line (right side, top to bottom) -->
            <svg class="absolute top-0 right-0 h-full w-auto" viewBox="0 0 270 594" fill="none"
                xmlns="http://www.w3.org/2000/svg" style="opacity: 0.15">
                <path d="M268.373 1.5C268.373 327.5 1.5 592.22 1.5 592.22" stroke="#B2EDA1" stroke-width="3"
                    stroke-linecap="round" fill="none" />
            </svg>

            <!-- Smaller curved element (top-right area) -->
            <svg class="absolute top-8 right-20 w-[287px] h-[339px]" viewBox="0 0 288 340" fill="none"
                xmlns="http://www.w3.org/2000/svg" style="opacity: 0.15">
                <path d="M286.37 1.5C286.37 186.5 1.5 338.27 1.5 338.27" stroke="#B2EDA1" stroke-width="3"
                    stroke-linecap="round" fill="none" />
            </svg>

            <!-- Small decorative circles -->
            <div class="absolute bottom-32 left-24 w-16 h-16 bg-[#B2EDA1] opacity-10 rounded-full" />
            <div class="absolute top-1/3 left-32 w-10 h-10 bg-[#B2EDA1] opacity-10 rounded-full" />
            <div class="absolute bottom-48 right-1/3 w-14 h-14 bg-[#B2EDA1] opacity-10 rounded-full" />
        </div>

        <UContainer class="relative z-10 py-20">
            <div class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-center">
                <!-- Left Content -->
                <div class="space-y-8">
                    <h1 class="text-5xl lg:text-[60px] font-bold text-white leading-tight lg:leading-[87.6px]">
                        Financial Security<br>
                        Made
                        <span class="relative inline-block text-[#B2EDA1]">
                            <span class="relative z-10">{{ currentWord }}</span>
                            <span class="absolute bottom-0 left-0 h-2 bg-[#B2EDA1] transition-all duration-100"
                                :style="{ width: `${progress}%` }" />
                        </span>
                    </h1>

                    <p class="text-base lg:text-lg text-gray-300 max-w-xl leading-[30px] font-medium">
                        Staco is the dedicated platform for human management that helps to grow your startup business
                        quickly
                    </p>

                    <div class="flex flex-wrap gap-4 items-center">
                        <!-- Primary Button -->
                        <button
                            class="inline-flex items-center justify-center px-8 py-4 bg-[#44C486] hover:bg-[#3AB377] text-white font-bold text-base rounded-full transition-colors leading-[30px]">
                            Get Start For Free
                        </button>

                        <!-- Secondary "Let's talk" Button -->
                        <button
                            class="inline-flex group items-center gap-3 px-6 py-3 text-white font-medium text-base hover:text-[#44C486] transition-all ease-in duration-100 leading-[30px]">
                            <span>Let's talk</span>
                            <span
                                class="flex items-center justify-center w-[30px] h-[30px] group-hover:rotate-[-45deg] group-hover:bg-[#44C486] group-hover:text-white transition-all ease-in duration-100 bg-white/10 rounded-[15px]">
                                <svg width="16" height="16" viewBox="0 0 16 16" fill="none"
                                    xmlns="http://www.w3.org/2000/svg">
                                    <path d="M6 12L10 8L6 4" stroke="white" stroke-width="2" stroke-linecap="round"
                                        stroke-linejoin="round" />
                                </svg>
                            </span>
                        </button>
                    </div>
                </div>

                <!-- Right Video -->
                <div class="flex justify-center lg:justify-end">
                    <HeroVideo />
                </div>
            </div>
        </UContainer>
    </section>
</template>
