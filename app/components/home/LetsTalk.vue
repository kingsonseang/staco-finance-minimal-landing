<script setup lang="ts">
const imageRef = ref<HTMLElement | null>(null)
const imageTransform = ref(0)

const updateImagePosition = () => {
  if (!imageRef.value) return

  const y = window.scrollY
  const elementOffset = imageRef.value.offsetTop
  const offsetStart = elementOffset - 400

  let animationValue = (y - offsetStart) / 4
  const animationStop = 100

  if (animationValue < 0) {
    animationValue = 0
  }

  if (animationValue > animationStop) {
    animationValue = animationStop
  }

  imageTransform.value = animationValue
}

onMounted(() => {
  window.addEventListener('scroll', updateImagePosition)
  updateImagePosition() // Initial calculation
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateImagePosition)
})
</script>

<template>
  <section class="max-md:px-4 py-12 bg-white">
    <UContainer>
      <div class="bg-[#004D42] rounded-[30px] px-8 lg:px-[70px] overflow-hidden">
        <div class="grid md:grid-cols-2 gap-12">
          <!-- Left Content -->
          <div class="pt-[54px] pb-[70px] max-md:text-center">
            <h2 class="text-white text-4xl lg:text-5xl font-bold mb-[34px] leading-tight">
              We are building<br>
              financial foundations
            </h2>

            <NuxtLink
              to="#"
              class="group inline-flex items-center gap-3 text-[#111111] hover:text-white font-bold bg-[#B2EDA1] hover:bg-[#44C486] px-6 py-3 rounded-full transition-colors duration-700"
            >
              <span>Let's Talk</span>
              <NuxtImg
                src="/images/icons/features-arrow-right.svg"
                alt="arrow"
                class="w-4 h-4 invert group-hover:invert-0 transition-all duration-700 group-hover:-rotate-45"
              />
            </NuxtLink>
          </div>

          <!-- Right Image -->
          <div class="flex items-end justify-end h-full">
            <div
              ref="imageRef"
              class="transition-transform duration-0 max-w-[372px] w-full align-middle"
              :style="{ transform: `translateY(${imageTransform}px)` }"
            >
              <NuxtImg
                src="/images/finance-index/lets-talk-img.svg"
                alt="Financial foundations illustration"
                class="w-full h-auto"
              />
            </div>
          </div>
        </div>
      </div>
    </UContainer>
  </section>
</template>
