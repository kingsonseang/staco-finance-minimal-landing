<script setup lang="ts">
import AnimatedLink from '~/components/ui/AnimatedLink.vue'

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
    { label: 'Careers', to: '#', badge: 'Hiring' }
  ]
}

const socialLinks = [
  { icon: '/images/icons/facebook.svg', to: '#', label: 'Facebook' },
  { icon: '/images/icons/twitter.svg', to: '#', label: 'Twitter' },
  { icon: '/images/icons/pinterest.svg', to: '#', label: 'Pinterest' },
  { icon: '/images/icons/instagram.svg', to: '#', label: 'Instagram' },
  { icon: '/images/icons/dribbble.svg', to: '#', label: 'Dribbble' }
]
</script>

<template>
  <div class="max-w-[1560px] px-4 lg:px-5 mx-auto">
    <footer class="bg-[#1F2334] rounded-[30px]">
      <!-- Footer Top -->
      <div class="pt-20 lg:pt-[120px] pb-16 lg:pb-[70px] md:px-8">
        <UContainer>
          <div class="grid lg:grid-cols-12 gap-8 justify-between">
            <!-- Left Column - Brand -->
            <div class="lg:col-span-3 md:col-span-6">
              <div class="mb-[58px]">
                <NuxtLink
                  to="/"
                  class="block mb-[37px]"
                >
                  <NuxtImg
                    src="/images/logo/finance-logo.svg"
                    alt="Staco Finance Logo"
                    class="h-10 w-auto"
                  />
                </NuxtLink>
                <p class="text-white/70 leading-relaxed">
                  Staco is the dedicated platform for performance management that helps to
                  grow your startup quickly
                </p>
              </div>

              <!-- Social Follow -->
              <div class="flex items-center gap-5">
                <p class="text-white mb-0 font-['Montserrat_Alternates']">
                  Follow:
                </p>
                <ul class="flex items-center gap-7 list-none">
                  <li
                    v-for="social in socialLinks"
                    :key="social.label"
                  >
                    <NuxtLink
                      :to="social.to"
                      class="transition-opacity hover:opacity-100"
                    >
                      <NuxtImg
                        :src="social.icon"
                        :alt="social.label"
                        class="w-4 h-4 opacity-70 hover:opacity-100 hover:scale-110 hover:-rotate-6 transition-all duration-300"
                      />
                    </NuxtLink>
                  </li>
                </ul>
              </div>
            </div>

            <!-- Right Column - Links Grid -->
            <div class="lg:col-span-8">
              <div class="grid md:grid-cols-4 grid-cols-2 gap-8">
                <!-- Products -->
                <div class="mt-[23px]">
                  <h6 class="uppercase font-semibold text-white mb-[25px]">
                    Products
                  </h6>
                  <ul class="space-y-5 list-none">
                    <li
                      v-for="link in footerLinks.products"
                      :key="link.label"
                    >
                      <AnimatedLink :to="link.to">
                        {{ link.label }}
                      </AnimatedLink>
                    </li>
                  </ul>
                </div>

                <!-- Why Choose -->
                <div class="mt-[23px]">
                  <h6 class="uppercase font-semibold text-white mb-[25px]">
                    Why choose
                  </h6>
                  <ul class="space-y-5 list-none">
                    <li
                      v-for="link in footerLinks.whyChoose"
                      :key="link.label"
                    >
                      <AnimatedLink :to="link.to">
                        {{ link.label }}
                      </AnimatedLink>
                    </li>
                  </ul>
                </div>

                <!-- Resources -->
                <div class="mt-[23px]">
                  <h6 class="uppercase font-semibold text-white mb-[25px]">
                    Resources
                  </h6>
                  <ul class="space-y-5 list-none">
                    <li
                      v-for="link in footerLinks.resources"
                      :key="link.label"
                    >
                      <AnimatedLink :to="link.to">
                        {{ link.label }}
                      </AnimatedLink>
                    </li>
                  </ul>
                </div>

                <!-- Company -->
                <div class="mt-[23px]">
                  <h6 class="uppercase font-semibold text-white mb-[25px]">
                    Company
                  </h6>
                  <ul class="space-y-5 list-none">
                    <li
                      v-for="link in footerLinks.company"
                      :key="link.label"
                    >
                      <AnimatedLink
                        :to="link.to"
                        class="inline-flex items-center gap-2"
                      >
                        {{ link.label }}
                        <span
                          v-if="link.badge"
                          class="bg-[#44C486] text-white text-xs px-2 py-0.5 rounded"
                        >
                          {{ link.badge }}
                        </span>
                      </AnimatedLink>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </UContainer>
      </div>

      <!-- Footer Bottom -->
      <div class="border-t border-white/10 py-[30px] md:px-8 max-md:text-sm max-md:text-center">
        <UContainer>
          <div class="grid md:grid-cols-12 gap-4">
            <div class="md:col-span-5 order-2 md:order-1">
              <p class="text-white/70 mb-0">
                2023 Staco. All rights reserved.
              </p>
            </div>
            <div class="md:col-span-7 order-1 md:order-2">
              <ul class="flex items-center justify-center md:justify-end gap-3 lg:gap-[30px] list-none flex-wrap">
                <li>
                  <NuxtLink
                    to="#"
                    class="text-white/70 hover:text-white transition-colors"
                  >
                    Terms and conditions
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink
                    to="#"
                    class="text-white/70 hover:text-white transition-colors"
                  >
                    Cookies
                  </NuxtLink>
                </li>
                <li>
                  <NuxtLink
                    to="#"
                    class="text-white/70 hover:text-white transition-colors"
                  >
                    Privacy policy
                  </NuxtLink>
                </li>
              </ul>
            </div>
          </div>
        </UContainer>
      </div>
    </footer>
  </div>
</template>
