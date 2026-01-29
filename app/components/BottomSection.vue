<script setup lang="ts">
import DisclaimerSection from '~/components/home/DisclaimerSection.vue'

const bottomSectionRef = ref<HTMLElement | null>(null)
const disclaimerRef = ref<HTMLElement | null>(null)

const updateDisclaimerPosition = () => {
  if (!bottomSectionRef.value || !disclaimerRef.value) return

  const y = window.scrollY
  const x = bottomSectionRef.value.offsetTop - 400

  if (y > x) {
    disclaimerRef.value.style.position = 'sticky'
    disclaimerRef.value.style.bottom = '0'
    disclaimerRef.value.style.zIndex = '-1'
  } else {
    disclaimerRef.value.style.position = 'unset'
  }
}

onMounted(() => {
  window.addEventListener('scroll', updateDisclaimerPosition)
  updateDisclaimerPosition()
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateDisclaimerPosition)
})
</script>

<template>
  <!-- Bottom Section Container -->
  <div
    ref="bottomSectionRef"
    class="bg-[#ECF1F1] relative z-1"
  >
    <slot />

    <!-- Disclaimer Section with Sticky Behavior -->
    <div
      ref="disclaimerRef"
      class="relative"
    >
      <DisclaimerSection />
    </div>
  </div>
</template>
