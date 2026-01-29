<script setup>
import FeatureCard from './FeatureCard.vue'

const features = [
  {
    icon: 'i-heroicons-server-stack',
    title: 'Used advanced technologies',
    description: 'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  },
  {
    icon: 'i-heroicons-pencil-square',
    title: 'Clean design & Typography',
    description: 'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  },
  {
    icon: 'i-heroicons-chat-bubble-left-right',
    title: 'Best customer support',
    description: 'I must explain to you how all this mistaken. Idea of main denouncing pleasure and praising pain was born',
    link: '#'
  }
]
</script>

<template>
  <section class="py-20 bg-gray-50">
    <UContainer>
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <FeatureCard
          v-for="(feature, index) in features"
          :key="index"
          :icon="feature.icon"
          :title="feature.title"
          :description="feature.description"
          :link="feature.link"
        />
      </div>
    </UContainer>
  </section>
</template>
