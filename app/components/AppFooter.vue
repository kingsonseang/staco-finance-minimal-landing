<script setup>
const footerLinks = {
  products: [
    { label: 'HR Management', to: '#' },
    { label: 'Invoice System', to: '#' },
    { label: 'Email Marketing', to: '#' },
    { label: 'Web Services', to: '#' },
    { label: 'Digital Marketing', to: '#' }
  ],
  whyChoose: [
    { label: 'Customers', to: '#' },
    { label: 'Why Staco ?', to: '#' },
    { label: 'Book a demo', to: '#' }
  ],
  resources: [
    { label: 'Latest Blog', to: '#' },
    { label: 'Supports', to: '#' },
    { label: 'Knowledgebase', to: '#' },
    { label: 'FAQs', to: '#' }
  ],
  company: [
    { label: 'About', to: '#' },
    { label: 'What we do', to: '#' },
    { label: 'Contact us', to: '#' },
    { label: 'Careers', to: '#' }
  ]
}

const socialLinks = [
  { icon: 'i-simple-icons-facebook', to: '#', label: 'Facebook' },
  { icon: 'i-simple-icons-x', to: '#', label: 'Twitter' },
  { icon: 'i-simple-icons-linkedin', to: '#', label: 'LinkedIn' },
  { icon: 'i-simple-icons-instagram', to: '#', label: 'Instagram' },
  { icon: 'i-simple-icons-youtube', to: '#', label: 'YouTube' }
]
</script>

<template>
  <footer class="bg-[#1F2334] text-white">
    <UContainer class="py-16 lg:py-20">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-12 gap-8 lg:gap-12">
        <!-- Brand Section -->
        <div class="lg:col-span-4 space-y-6">
          <AppLogo class="h-10 w-auto" />
          <p class="text-white/70 text-[15px] leading-[30px] max-w-[320px] font-medium">
            Staco is the dedicated platform for performance management that helps to grow your startup
            quickly
          </p>
          <div class="flex gap-3">
            <UButton
              v-for="social in socialLinks"
              :key="social.label"
              :icon="social.icon"
              :to="social.to"
              variant="ghost"
              color="white"
              size="md"
              class="rounded-full w-10 h-10 p-0 flex items-center justify-center border border-white/20 hover:bg-white/10"
              :aria-label="social.label"
            />
          </div>
        </div>

        <!-- Products Column -->
        <div class="lg:col-span-2">
          <h3 class="font-extrabold text-[15px] uppercase tracking-wide mb-6 flex items-center gap-2">
            PRODUCTS
            <span class="text-lg">🔥</span>
          </h3>
          <ul class="space-y-4">
            <li
              v-for="link in footerLinks.products"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-white/70 hover:text-white transition-colors text-[15px] leading-[30px] font-medium inline-block"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Why Choose Column -->
        <div class="lg:col-span-2">
          <h3 class="font-extrabold text-[15px] uppercase tracking-wide mb-6 flex items-center gap-2">
            WHY CHOOSE
            <span class="text-lg">💛</span>
          </h3>
          <ul class="space-y-4">
            <li
              v-for="link in footerLinks.whyChoose"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-white/70 hover:text-white transition-colors text-[15px] leading-[30px] font-medium inline-block"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Resources Column -->
        <div class="lg:col-span-2">
          <h3 class="font-extrabold text-[15px] uppercase tracking-wide mb-6 flex items-center gap-2">
            RESOURCES
            <span class="text-lg">🎯</span>
          </h3>
          <ul class="space-y-4">
            <li
              v-for="link in footerLinks.resources"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-white/70 hover:text-white transition-colors text-[15px] leading-[30px] font-medium inline-block"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Company Column -->
        <div class="lg:col-span-2">
          <h3 class="font-extrabold text-[15px] uppercase tracking-wide mb-6 flex items-center gap-2">
            COMPANY
            <span class="text-lg">💙</span>
          </h3>
          <ul class="space-y-4">
            <li
              v-for="link in footerLinks.company"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-white/70 hover:text-white transition-colors text-[15px] leading-[30px] font-medium inline-block"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div
        class="mt-16 pt-8 border-t border-white/10 flex flex-col md:flex-row justify-between items-center gap-4"
      >
        <p class="text-white/70 text-[15px] font-medium">
          2023 Staco. All rights reserved.
        </p>
        <div class="flex flex-wrap gap-6 text-[15px]">
          <NuxtLink
            to="#"
            class="text-white/70 hover:text-white transition-colors font-medium"
          >
            Terms and conditions
          </NuxtLink>
          <NuxtLink
            to="#"
            class="text-white/70 hover:text-white transition-colors font-medium"
          >
            Cookies
          </NuxtLink>
          <NuxtLink
            to="#"
            class="text-white/70 hover:text-white transition-colors font-medium"
          >
            Privacy policy
          </NuxtLink>
        </div>
      </div>
    </UContainer>
  </footer>
</template>
