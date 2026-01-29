<script setup lang="ts">
import OliveButton from './ui/OliveButton.vue'

const isMobileMenuOpen = ref(false)

const tabs = ref([
  { label: 'Home', value: '/' },
  { label: 'About', value: '/about' },
  { label: 'Services', value: '#' },
  { label: 'Blogs', value: '#' },
  { label: 'Contact us', value: '#' }
])

// Language selector
const selectedLanguage = ref('EN')
const isLanguageOpen = ref(false)

const languages = [
  { code: 'EN', name: 'English (US)' },
  { code: 'EN', name: 'English (UK)' },
  { code: 'ES', name: 'Español' },
  { code: 'FR', name: 'Français' },
  { code: 'Tü', name: 'Türkçe' },
  { code: '简体', name: '简体中文' },
  { code: 'ITA', name: 'Italiano' },
  { code: 'العر', name: 'العربية' }
]

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
  if (isMobileMenuOpen.value) {
    document.body.classList.add('nav-expanded')
  } else {
    document.body.classList.remove('nav-expanded')
  }
}

onUnmounted(() => {
  document.body.classList.remove('nav-expanded')
})
</script>

<template>
  <div class="absolute top-0 left-0 right-0 z-50 pt-6">
    <div class="container mx-auto flex items-center justify-between px-6 md:justify-center gap-4">
      <!-- Logo -->
      <AppLogo class="h-12 md:h- w-auto" />

      <!-- Desktop Navigation with Bubble -->
      <div class="max-md:hidden nav-wrap">
        <div
          class="bubble active"
          aria-hidden="true"
        />
        <div
          class="bubble hover"
          aria-hidden="true"
        />
        <nav
          class="nav"
          aria-label="Main navigation"
        >
          <NuxtLink
            v-for="tab in tabs"
            :key="tab.value"
            :to="tab.value"
          >
            {{ tab.label }}
          </NuxtLink>
        </nav>
      </div>

      <!-- Desktop Right Actions -->
      <div class="max-md:hidden flex items-center gap-4">
        <!-- Language Dropdown -->
        <div class="relative">
          <button
            type="button"
            class="flex items-center gap-2 text-white hover:text-white/70 transition-colors focus-visible:outline-2 focus-visible:outline-white focus-visible:outline-offset-2"
            :aria-expanded="isLanguageOpen"
            aria-label="Select language"
            aria-controls="language-menu"
            @click="isLanguageOpen = !isLanguageOpen"
          >
            <NuxtImg
              src="/images/icons/global-gray.svg"
              alt="language"
              class="w-5 h-5"
            />
            <span>{{ selectedLanguage }}</span>
          </button>

          <!-- Language Dropdown Menu -->
          <div
            v-if="isLanguageOpen"
            id="language-menu"
            role="menu"
            aria-label="Language options"
            class="absolute top-full right-0 mt-2 w-48 bg-white rounded-lg shadow-lg border border-black/10 py-2 z-50"
          >
            <button
              v-for="(lang, index) in languages"
              :key="index"
              type="button"
              role="menuitem"
              class="w-full px-4 py-2 text-left hover:bg-gray-100 transition-colors flex items-center justify-between focus-visible:outline-2 focus-visible:outline-green-500 focus-visible:bg-gray-50"
              :aria-label="`Select ${lang.name}`"
              @click="selectedLanguage = lang.code; isLanguageOpen = false"
            >
              <span class="font-bold text-[#111111]">{{ lang.code }}</span>
              <span class="text-[#444444] text-sm">{{ lang.name }}</span>
            </button>
          </div>
        </div>

        <!-- Sign In -->
        <NuxtLink
          to="/sign-in"
          class="text-white hover:text-white/70 transition-colors"
        >
          Sign in
        </NuxtLink>

        <!-- Start Free Button -->
        <OliveButton
          to="/sign-up"
          class="!h-12 !w-[120px]"
        >
          Start Free
        </OliveButton>
      </div>

      <!-- Mobile Menu Toggle -->
      <div class="md:hidden">
        <button
          type="button"
          class="flex items-center justify-center focus-visible:outline-2 focus-visible:outline-white focus-visible:outline-offset-2 p-2"
          :aria-expanded="isMobileMenuOpen"
          aria-label="Toggle mobile menu"
          aria-controls="mobile-nav"
          @click="toggleMobileMenu"
        >
          <Icon
            v-if="!isMobileMenuOpen"
            name="heroicons-solid:menu"
            class="h-6 w-6 text-white"
          />
          <Icon
            v-else
            name="heroicons-solid:x"
            class="h-6 w-6 text-white"
          />
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <nav
      id="mobile-nav"
      aria-label="Mobile navigation"
      class="md:hidden fixed top-0 left-0 w-full bg-white shadow-[0px_5px_15px_rgba(0,0,0,0.1)] pt-[70px] pb-5 overflow-y-auto transition-transform duration-300 z-[999]"
      :class="isMobileMenuOpen ? 'translate-y-0' : '-translate-y-full'"
      :aria-hidden="!isMobileMenuOpen"
    >
      <div class="max-w-[720px] mx-auto px-2">
        <!-- Mobile Nav Menu -->
        <ul class="list-none m-0 p-0">
          <li
            v-for="tab in tabs"
            :key="tab.value"
            class="border-b border-black/10"
          >
            <NuxtLink
              :to="tab.value"
              class="block py-4 text-[#111111] font-medium hover:text-[#0095ff] transition-colors"
              @click="toggleMobileMenu"
            >
              {{ tab.label }}
            </NuxtLink>
          </li>
        </ul>

        <!-- Mobile Buttons -->
        <div class="flex items-center gap-4 mt-5">
          <NuxtLink
            to="/sign-in"
            class="flex-1 text-center bg-black/5 rounded-[50px] px-12 py-3 font-bold text-[#111111] hover:bg-[#0095ff] hover:text-white transition-colors"
          >
            Sign in
          </NuxtLink>
          <OliveButton
            to="/sign-up"
            class="flex-1"
          >
            Start Free
          </OliveButton>
        </div>
      </div>
    </nav>

    <!-- Overlay -->
    <div
      v-if="isMobileMenuOpen"
      class="fixed inset-0 bg-black/50 z-998"
      role="button"
      tabindex="0"
      aria-label="Close mobile menu"
      @click="toggleMobileMenu"
      @keydown.enter="toggleMobileMenu"
      @keydown.space.prevent="toggleMobileMenu"
    />
  </div>
</template>
