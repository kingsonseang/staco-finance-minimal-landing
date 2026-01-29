<script setup>
import HeroSection from '~/components/home/HeroSection.vue'
import FeaturesSection from '~/components/home/FeaturesSection.vue'
import LetsTalk from '~/components/home/LetsTalk.vue'
import TeamSection from '~/components/home/TeamSection.vue'
import TestimonialsSection from '~/components/home/TestimonialsSection.vue'
import BottomSection from '~/components/home/BottomSection.vue'
import AppFooter from '~/components/AppFooter.vue'
</script>

<template>
  <div class="bg-white">
    <HeroSection />
    <FeaturesSection />
    <LetsTalk />
    <TeamSection />

    <BottomSection>
      <TestimonialsSection />
      <AppFooter />
    </BottomSection>
  </div>
</template>
