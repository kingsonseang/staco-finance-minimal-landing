<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// Slider state
const currentSlide = ref(0)
const progress = ref(0)
const intervalDuration = 10000 // 10 seconds
let autoPlayInterval = null
let progressInterval = null

// Slide data extracted from the provided HTML
const slides = [
    {
        title: 'Discover business Opportunities',
        description: 'We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.',
        features: [
            'Profile Consultation',
            'Asset management',
            'No-risk business idea'
        ]
    },
    {
        title: 'Manage team increase productivity',
        description: 'We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.',
        features: [
            '99% Survey Report',
            'Trusted by teams',
            'Self-Service'
        ]
    },
    {
        title: 'Manage team increase productivity',
        description: 'We use as filler text for layouts, non-readability is of great importance but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful nor again is there anyone.',
        features: [
            '99% Survey Report',
            'Trusted by teams',
            'Self-Service'
        ]
    }
]

// Image data - using placeholder images (replace with actual team images)
const images = [
    'https://images.unsplash.com/photo-1600880292203-757bb62b4baf?w=400&h=600&fit=crop',
    'https://images.unsplash.com/photo-1573497019940-1c28c88b4f3e?w=400&h=600&fit=crop',
    'https://images.unsplash.com/photo-1556157382-97eda2d62296?w=600&h=600&fit=crop'
]

// Start progress animation
const startProgress = () => {
    progress.value = 0
    const progressStep = 100 / (intervalDuration / 50) // Update every 50ms

    progressInterval = setInterval(() => {
        progress.value += progressStep
        if (progress.value >= 100) {
            progress.value = 100
        }
    }, 50)
}

// Restart timers
const restartTimers = () => {
    // Clear existing intervals
    if (autoPlayInterval) clearInterval(autoPlayInterval)
    if (progressInterval) clearInterval(progressInterval)

    // Start new intervals
    startProgress()
    autoPlayInterval = setInterval(() => {
        currentSlide.value = (currentSlide.value + 1) % slides.length
        startProgress()
    }, intervalDuration)
}

// Handle image click
const goToSlide = (index) => {
    currentSlide.value = index
    restartTimers()
}

// Lifecycle hooks
onMounted(() => {
    restartTimers()
})

onUnmounted(() => {
    if (autoPlayInterval) clearInterval(autoPlayInterval)
    if (progressInterval) clearInterval(progressInterval)
})
</script>

<template>
    <section class="py-20 bg-white">
        <UContainer>
            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <!-- Left: Text Content Slider -->
                <div class="space-y-6">
                    <span class="inline-block text-[#0095FF] text-sm font-bold tracking-[3.6px] uppercase">
                        WHY CHOOSE US
                    </span>

                    <!-- Content transitions -->
                    <Transition name="fade" mode="out-in">
                        <div :key="currentSlide" class="space-y-6">
                            <h2 class="text-4xl lg:text-5xl font-bold text-[#111111] leading-tight">
                                {{ slides[currentSlide].title }}
                            </h2>

                            <p class="text-base text-[#444444] leading-relaxed">
                                {{ slides[currentSlide].description }}
                            </p>

                            <ul class="space-y-3">
                                <li v-for="(feature, index) in slides[currentSlide].features" :key="index"
                                    class="flex items-start gap-3">
                                    <UIcon name="i-heroicons-check"
                                        class="w-5 h-5 text-[#0EC36B] flex-shrink-0 mt-0.5" />
                                    <span class="text-[#444444]">{{ feature }}</span>
                                </li>
                            </ul>
                        </div>
                    </Transition>
                </div>

                <!-- Right: Image Gallery with Controls -->
                <div class="flex gap-4 items-center justify-end">
                    <div v-for="(image, index) in images" :key="index" @click="goToSlide(index)"
                        class="relative cursor-pointer transition-all duration-500 rounded-2xl overflow-hidden group"
                        :class="{
                            'w-30 h-96': index !== currentSlide,
                            'w-full min-w-56 h-96': index === currentSlide
                        }">
                        <!-- Image -->
                        <img :src="image" :alt="`Team member ${index + 1}`"
                            class="w-full h-full object-cover transition-transform duration-300 group-hover:scale-105" />

                        <!-- Overlay on hover for inactive images -->
                        <div
                            class="absolute inset-0 bg-black/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                        </div>

                        <!-- Progress bar for active image -->
                        <!-- <div v-if="index === currentSlide" class="absolute bottom-0 left-0 right-0 h-1 bg-black/30">
                            <div class="h-full bg-white transition-all duration-100"
                                :style="{ width: `${progress}%` }" />
                        </div> -->
                    </div>
                </div>
            </div>
        </UContainer>
    </section>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
