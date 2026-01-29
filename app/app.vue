<script setup>
// import AppNav from './components/AppNav.vue'
// import AppFooter from './components/AppFooter.vue'

useHead({
  meta: [{ name: 'viewport', content: 'width=device-width, initial-scale=1' }],
  link: [
    { rel: 'icon', href: '/favicon.ico' },
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' },
    {
      rel: 'stylesheet',
      href: 'https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;700&family=Plus+Jakarta+Sans:wght@700&Montserrat+Alternates:ital,wght@0,300;&display=swap'
    }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Staco Finance'
const description
  = 'A dedicated platform for human management that helps to grow your startup business quickly'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description
})
</script>

<template>
  <UApp>
    <!-- <AppNav /> -->

    <UMain>
      <NuxtPage />
    </UMain>

    <!-- <AppFooter /> -->
  </UApp>
</template>
