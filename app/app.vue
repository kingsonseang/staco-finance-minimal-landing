<script setup>
import AppNav from './components/AppNav.vue';

useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '/favicon.ico' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Staco Finance'
const description = 'A dedicated platform for human management that helps to grow your startup business quickly'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description
})
</script>

<template>
  <UApp>
    <AppNav />

    <UMain>
      <NuxtPage />
    </UMain>

    <UFooter>
      footer goes here
    </UFooter>
  </UApp>
</template>
