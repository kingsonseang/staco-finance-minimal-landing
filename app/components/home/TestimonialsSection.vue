<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// Carousel state
const currentIndex = ref(0)
const isPaused = ref(false)
const rotationDuration = 8000 // 8 seconds
let rotationInterval = null

// Testimonials data
const testimonials = [
  {
    quote: 'I must explain to you how all this mistaken. Idea of denouncing pleasure and praising pain was born and I will give you a complete account. 😃',
    author: 'Roe Smith',
    role: 'Director, Growth Marketing',
    image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&h=500&fit=crop'
  },
  {
    quote: 'The system is incredibly intuitive and has transformed the way we approach our business challenges. Highly recommend to anyone looking to scale efficiently! 🚀',
    author: 'Sarah Johnson',
    role: 'CEO, Tech Innovations',
    image: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=400&h=500&fit=crop'
  },
  {
    quote: 'Working with this platform has been a game-changer for our team. The results speak for themselves and we couldn\'t be happier with our decision. 💼',
    author: 'Michael Chen',
    role: 'Product Manager, StartupCo',
    image: 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=400&h=500&fit=crop'
  },
  {
    quote: 'Exceptional service and support throughout our journey. They truly understand what businesses need to succeed in today\'s competitive market. ⭐',
    author: 'Emily Rodriguez',
    role: 'Founder, Creative Studio',
    image: 'https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=400&h=500&fit=crop'
  }
]

// Company logos - using placeholder text for now (replace with actual logo images)
const companies = [
  { name: 'jQuery', image: 'https://via.placeholder.com/80x30/CCCCCC/666666?text=jQuery' },
  { name: 'GitHub', image: 'https://via.placeholder.com/80x30/CCCCCC/666666?text=GitHub' },
  { name: 'Portis', image: 'https://via.placeholder.com/80x30/CCCCCC/666666?text=Portis' },
  { name: 'Envato', image: 'https://via.placeholder.com/80x30/CCCCCC/666666?text=Envato' },
  { name: 'Daomak', image: 'https://via.placeholder.com/80x30/CCCCCC/666666?text=Daomak' }
]

// Start rotation
const startRotation = () => {
  if (rotationInterval) clearInterval(rotationInterval)

  rotationInterval = setInterval(() => {
    if (!isPaused.value) {
      goToNext()
    }
  }, rotationDuration)
}

// Navigation functions
const goToNext = () => {
  currentIndex.value = (currentIndex.value + 1) % testimonials.length
}

const goTo = (index) => {
  currentIndex.value = index
  startRotation() // Restart timer on manual navigation
}

// Pause/Resume handlers
const handleMouseEnter = () => {
  isPaused.value = true
}

const handleMouseLeave = () => {
  isPaused.value = false
}

// Lifecycle hooks
onMounted(() => {
  startRotation()
})

onUnmounted(() => {
  if (rotationInterval) clearInterval(rotationInterval)
})
</script>

<template>
  <section class="py-20 bg-[#F5F5F5]">
    <UContainer>
      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Left: Profile Image with Decorative Elements -->
        <div
          class="relative"
          @mouseenter="handleMouseEnter"
          @mouseleave="handleMouseLeave"
        >
          <!-- Decorative arc background -->
          <div
            class="absolute -left-8 top-0 w-64 h-80 bg-[#004D42] rounded-tr-[200px]"
            style="clip-path: ellipse(60% 100% at 0% 50%);"
          />

          <!-- Profile image container with transition -->
          <div class="relative ml-16">
            <div class="w-72 h-80 bg-[#B2EDA1] rounded-t-full overflow-hidden">
              <Transition
                name="fade"
                mode="out-in"
              >
                <img
                  :key="currentIndex"
                  :src="testimonials[currentIndex].image"
                  :alt="testimonials[currentIndex].author"
                  class="w-full h-full object-cover object-top"
                >
              </Transition>
            </div>
          </div>
        </div>

        <!-- Right: Testimonial Content -->
        <div
          class="space-y-6 relative"
          @mouseenter="handleMouseEnter"
          @mouseleave="handleMouseLeave"
        >
          <!-- Quote icon -->
          <div
            class="absolute -top-4 right-0 w-16 h-16 bg-gradient-to-br from-[#44C486] to-[#0EC36B] rounded-full flex items-center justify-center"
          >
            <span class="text-white text-2xl font-bold">"</span>
          </div>

          <!-- Content with transitions -->
          <Transition
            name="fade"
            mode="out-in"
          >
            <div
              :key="currentIndex"
              class="space-y-6"
            >
              <blockquote
                class="text-base text-[#111111] leading-[30px] font-medium pt-12"
                style="font-family: 'DM Sans', sans-serif;"
              >
                {{ testimonials[currentIndex].quote }}
              </blockquote>

              <div class="space-y-1">
                <p
                  class="text-lg font-bold text-[#111111]"
                  style="font-family: 'DM Sans', sans-serif;"
                >
                  {{ testimonials[currentIndex].author }}
                </p>
                <p
                  class="text-base text-[#444444] font-medium"
                  style="font-family: 'DM Sans', sans-serif;"
                >
                  {{ testimonials[currentIndex].role }}
                </p>
              </div>
            </div>
          </Transition>

          <!-- Navigation Dots -->
          <div class="flex items-center gap-3 pt-4">
            <button
              v-for="(testimonial, index) in testimonials"
              :key="index"
              class="transition-all duration-300"
              :class="index === currentIndex
                ? 'w-8 h-2 bg-[#44C486] rounded-full'
                : 'w-2 h-2 bg-gray-400 rounded-full hover:bg-gray-600'"
              :aria-label="`Go to testimonial ${index + 1}`"
              @click="goTo(index)"
            />
          </div>

          <!-- Company Logos -->
          <div class="flex flex-wrap items-center gap-8 pt-8 border-t border-gray-300">
            <img
              v-for="(company, index) in companies"
              :key="index"
              :src="company.image"
              :alt="company.name"
              class="h-8 opacity-40 hover:opacity-60 transition-opacity grayscale"
            >
          </div>
        </div>
      </div>
    </UContainer>
  </section>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
