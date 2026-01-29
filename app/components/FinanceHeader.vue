<script setup lang="ts">
import OliveButton from './ui/OliveButton.vue'

// const isMenuOpen = ref(false)
const isMobileMenuOpen = ref(false)
const isSticky = ref(false)

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

// Handle sticky header on scroll
let lastScrollPos = 0

const handleScroll = () => {
  const scrollPos = window.scrollY

  if (scrollPos > 100) {
    // Only hide header when scrolling down past 100px
    if (scrollPos > lastScrollPos) {
      isSticky.value = false
    } else {
      // Show header when scrolling up
      isSticky.value = true
    }
  } else {
    // Not scrolled enough, hide sticky header
    isSticky.value = false
  }

  lastScrollPos = scrollPos
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
  if (isMobileMenuOpen.value) {
    document.body.classList.add('nav-expanded')
  } else {
    document.body.classList.remove('nav-expanded')
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  document.body.classList.remove('nav-expanded')
})
</script>

<template>
  <header
    class="fixed top-0 left-0 z-9999 py-[15px] transition-all duration-300 w-screen overflow-clip"
  >
    <UContainer>
      <div
        class="bg-white/10 backdrop-blur-[2.5px] rounded-[40px] h-20 px-[15px] py-[10px] pb-[15px] transition-all flex items-center"
      >
        <nav class="flex items-center justify-between gap-[60px] w-full">
          <!-- Logo -->
          <NuxtLink
            to="/"
            class="shrink-0 h-full"
          >
            <NuxtImg
              src="/images/logo/finance-logo.svg"
              alt="Finance Logo"
              class="h-full w-auto"
            />
          </NuxtLink>

          <!-- Mobile Menu Toggle -->
          <button
            class="lg:hidden flex items-center justify-center"
            @click="toggleMobileMenu"
          >
            <NuxtImg
              v-if="!isMobileMenuOpen"
              src="/images/icons/menu.svg"
              alt="menu"
              class="w-6 h-6"
            />
            <NuxtImg
              v-else
              src="/images/icons/menu-close.svg"
              alt="close"
              class="w-6 h-6"
            />
          </button>

          <!-- Desktop Navigation -->
          <div class="hidden lg:flex items-center justify-between flex-1 gap-[30px]">
            <!-- Main Menu -->
            <ul class="flex items-center gap-[30px] list-none m-0 p-0">
              <li class="relative group">
                <NuxtLink
                  to="/"
                  class="text-white py-[15px] font-medium transition-colors hover:text-white/70"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                >
                  Home
                </NuxtLink>
              </li>
              <li class="relative group">
                <NuxtLink
                  to="/pages"
                  class="text-white py-[15px] font-medium transition-colors hover:text-white/70"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                >
                  Pages
                </NuxtLink>
              </li>
              <li>
                <NuxtLink
                  to="/services"
                  class="text-white py-[15px] font-medium transition-colors hover:text-white/70"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                >
                  Services
                </NuxtLink>
              </li>
              <li>
                <NuxtLink
                  to="/blog"
                  class="text-white py-[15px] font-medium transition-colors hover:text-white/70"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                >
                  Blogs
                </NuxtLink>
              </li>
              <li>
                <NuxtLink
                  to="/contact"
                  class="text-white py-[15px] font-medium transition-colors hover:text-white/70"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                >
                  Contact us
                </NuxtLink>
              </li>
            </ul>

            <!-- Header Extra -->
            <ul class="flex items-center gap-[30px] list-none m-0 p-0">
              <!-- Language Dropdown -->
              <li class="relative">
                <button
                  class="flex items-center gap-2 text-white hover:text-white/70 transition-colors"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                  @click="isLanguageOpen = !isLanguageOpen"
                >
                  <NuxtImg
                    src="/images/icons/global-gray.svg"
                    alt="language"
                    class="w-5 h-5"
                    :class="{ 'brightness-0': isSticky }"
                  />
                  <span>{{ selectedLanguage }}</span>
                </button>

                <!-- Language Dropdown Menu -->
                <div
                  v-if="isLanguageOpen"
                  class="absolute top-full right-0 mt-2 w-48 bg-white rounded-lg shadow-lg border border-black/10 py-2 z-50"
                >
                  <button
                    v-for="(lang, index) in languages"
                    :key="index"
                    class="w-full px-4 py-2 text-left hover:bg-gray-100 transition-colors flex items-center justify-between"
                    @click="selectedLanguage = lang.code; isLanguageOpen = false"
                  >
                    <span class="font-bold text-[#111111]">{{ lang.code }}</span>
                    <span class="text-[#444444] text-sm">{{ lang.name }}</span>
                  </button>
                </div>
              </li>

              <!-- Sign In -->
              <li>
                <NuxtLink
                  to="/sign-in"
                  class="text-white hover:text-white/70 transition-colors"
                  :class="{ 'text-[#111111] hover:text-[#444444]': isSticky }"
                >
                  Sign in
                </NuxtLink>
              </li>

              <!-- Start Free Button -->
              <li>
                <OliveButton
                  to="/sign-up"
                  class="!h-12 !w-30"
                >
                  Start Free
                </OliveButton>
              </li>
            </ul>
          </div>
        </nav>
      </div>
    </UContainer>

    <!-- Mobile Menu -->
    <nav
      class="lg:hidden fixed top-0 left-0 w-full bg-white shadow-[0px_5px_15px_rgba(0,0,0,0.1)] pt-[70px] pb-5 overflow-y-auto transition-transform duration-300 z-[999]"
      :class="isMobileMenuOpen ? 'translate-y-0' : '-translate-y-full'"
    >
      <div class="max-w-[720px] mx-auto px-2">
        <!-- Mobile Nav Menu -->
        <ul class="list-none m-0 p-0">
          <li class="border-b border-black/10">
            <NuxtLink
              to="/"
              class="block py-4 text-[#111111] font-medium hover:text-[#0095ff] transition-colors"
              @click="toggleMobileMenu"
            >
              Home
            </NuxtLink>
          </li>
          <li class="border-b border-black/10">
            <NuxtLink
              to="/pages"
              class="block py-4 text-[#111111] font-medium hover:text-[#0095ff] transition-colors"
              @click="toggleMobileMenu"
            >
              Pages
            </NuxtLink>
          </li>
          <li class="border-b border-black/10">
            <NuxtLink
              to="/services"
              class="block py-4 text-[#111111] font-medium hover:text-[#0095ff] transition-colors"
              @click="toggleMobileMenu"
            >
              Service
            </NuxtLink>
          </li>
          <li class="border-b border-black/10">
            <NuxtLink
              to="/blog"
              class="block py-4 text-[#111111] font-medium hover:text-[#0095ff] transition-colors"
              @click="toggleMobileMenu"
            >
              Blog
            </NuxtLink>
          </li>
          <li class="border-b border-black/10">
            <NuxtLink
              to="/contact"
              class="block py-4 text-[#111111] font-medium hover:text-[#0095ff] transition-colors"
              @click="toggleMobileMenu"
            >
              Contact Us
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
      class="fixed inset-0 bg-black/50 z-[998]"
      @click="toggleMobileMenu"
    />
  </header>
</template>
