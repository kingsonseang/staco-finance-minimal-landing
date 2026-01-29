<script setup lang="ts">
const tabs = ref([
  { label: 'Home', value: '/' },
  { label: 'About', value: '/about' },
  { label: 'Services', value: '/our-services' },
  { label: 'Blogs', value: '/blog' },
  { label: 'Contact us', value: '/contact-us' }
])
</script>

<template>
  <div class="absolute top-0 left-0 right-0 z-50 pt-6">
    <div class="md:w-fit w-full mx-auto flex items-center justify-between px-6 md:justify-center gap-4">
      <AppLogo class="size-12 md:size-16" />

      <div class="max-md:hidden nav-wrap">
        <div class="bubble active" />
        <div class="bubble hover" />
        <nav class="nav">
          <NuxtLink
            v-for="tab in tabs"
            :key="tab.value"
            :to="tab.value"
          >
            {{ tab.label }}
          </NuxtLink>
        </nav>
      </div>

      <div class="md:hidden">
        <Icon
          name="heroicons-solid:menu"
          class="h-6 w-6"
        />
      </div>
    </div>
  </div>
</template>
