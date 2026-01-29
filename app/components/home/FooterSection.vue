<script setup>
const footerLinks = {
  product: [
    { label: 'Staco Credit', to: '#' },
    { label: 'Staco Payment', to: '#' },
    { label: 'Marketplace', to: '#' },
    { label: 'Staco Services', to: '#' }
  ],
  information: [
    { label: 'Blog', to: '#' },
    { label: 'Support', to: '#' },
    { label: 'Get in touch', to: '#' }
  ],
  resources: [
    { label: 'Help center', to: '#' },
    { label: 'Partners', to: '#' },
    { label: 'Community', to: '#' }
  ],
  company: [
    { label: 'About us', to: '#' },
    { label: 'Careers', to: '#' },
    { label: 'News room', to: '#' }
  ]
}

const socialLinks = [
  { icon: 'i-simple-icons-facebook', to: '#', label: 'Facebook' },
  { icon: 'i-simple-icons-twitter', to: '#', label: 'Twitter' },
  { icon: 'i-simple-icons-instagram', to: '#', label: 'Instagram' },
  { icon: 'i-simple-icons-linkedin', to: '#', label: 'LinkedIn' },
  { icon: 'i-simple-icons-youtube', to: '#', label: 'YouTube' }
]
</script>

<template>
  <footer class="bg-[#1F2334] text-white">
    <UContainer class="py-16">
      <div class="grid md:grid-cols-2 lg:grid-cols-6 gap-12">
        <!-- Brand Section -->
        <div class="lg:col-span-2 space-y-4">
          <AppLogo class="h-12 w-auto" />
          <p class="text-gray-400 text-sm leading-relaxed max-w-sm">
            We denounce with righteous indige nation in and dislike men who are so beguiled and to demo
            realized by the charms of pleasure
          </p>
          <div class="flex gap-4">
            <UButton
              v-for="social in socialLinks"
              :key="social.label"
              :icon="social.icon"
              :to="social.to"
              variant="ghost"
              color="white"
              size="sm"
              :aria-label="social.label"
            />
          </div>
        </div>

        <!-- Product Links -->
        <div>
          <h3 class="font-bold text-lg mb-4">
            Product
          </h3>
          <ul class="space-y-3">
            <li
              v-for="link in footerLinks.product"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-gray-400 hover:text-white transition-colors text-sm"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Information Links -->
        <div>
          <h3 class="font-bold text-lg mb-4">
            Information
          </h3>
          <ul class="space-y-3">
            <li
              v-for="link in footerLinks.information"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-gray-400 hover:text-white transition-colors text-sm"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Resources Links -->
        <div>
          <h3 class="font-bold text-lg mb-4">
            Resources
          </h3>
          <ul class="space-y-3">
            <li
              v-for="link in footerLinks.resources"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-gray-400 hover:text-white transition-colors text-sm"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Company Links -->
        <div>
          <h3 class="font-bold text-lg mb-4">
            Company
          </h3>
          <ul class="space-y-3">
            <li
              v-for="link in footerLinks.company"
              :key="link.label"
            >
              <NuxtLink
                :to="link.to"
                class="text-gray-400 hover:text-white transition-colors text-sm"
              >
                {{ link.label }}
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div
        class="mt-12 pt-8 border-t border-white/10 flex flex-col md:flex-row justify-between items-center gap-4"
      >
        <p class="text-gray-400 text-sm">
          © 2024 Staco. All rights reserved
        </p>
        <div class="flex gap-6 text-sm">
          <NuxtLink
            to="#"
            class="text-gray-400 hover:text-white transition-colors"
          >
            Terms of Service
          </NuxtLink>
          <NuxtLink
            to="#"
            class="text-gray-400 hover:text-white transition-colors"
          >
            Privacy Policy
          </NuxtLink>
        </div>
      </div>
    </UContainer>
  </footer>
</template>
