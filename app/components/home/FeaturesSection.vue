<script setup>
import FeatureCard from '../ui/FeatureCard.vue'

const features = [
  {
    image: '/images/finance-index/subtitle.svg',
    title: 'Used advanced technologies',
    description: 'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  },
  {
    image: '/images/finance-index/mask.svg',
    title: 'Clean design & Typography',
    description: 'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  },
  {
    image: '/images/finance-index/archive-book.svg',
    title: 'Best customer support',
    description: 'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  }
]
</script>

<template>
  <section class="py-20">
    <UContainer>
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <FeatureCard
          v-for="(feature, index) in features"
          :key="index"
          :image="feature.image"
          :title="feature.title"
          :description="feature.description"
          :link="feature.link"
        />
      </div>
    </UContainer>
  </section>
</template>
