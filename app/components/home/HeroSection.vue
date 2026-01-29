<script setup>
import OliveButton from '../ui/OliveButton.vue'
import HeroVideo from './HeroVideo.vue'
import AnimatedWords from '~/components/ui/AnimatedWords.vue'
</script>

<template>
  <section class="relative bg-[#1F2334] overflow-hidden lg:mb-20">
    <span class="absolute top-[30%] left-[20%]"><NuxtImg
      src="/images/finance-index/Vector-1.svg"
      alt="img"
      class="max-w-full align-middle"
    /></span>
    <span class="absolute left-[44%] bottom-[35%]"><NuxtImg
      src="/images/finance-index/Vector-2.svg"
      alt="img"
      class="max-w-full align-middle"
    /></span>
    <span class="absolute left-[45%] bottom-[18%]"><NuxtImg
      src="/images/finance-index/Vector-3.svg"
      alt="img"
      class="max-w-full align-middle"
    /></span>
    <span class="absolute right-[40%] top-[56%]"><NuxtImg
      src="/images/finance-index/Vector-4.svg"
      alt="img"
      class="max-w-full align-middle"
    /></span>
    <span class="absolute left-1/4 bottom-[13%]"><NuxtImg
      src="/images/finance-index/Vector-5.svg"
      alt="img"
      class="max-w-full align-middle"
    /></span>
    <span class="absolute left-1/4 top-[18%]"><NuxtImg
      src="/images/finance-index/Vector-6.svg"
      alt="img"
      class="max-w-full align-middle"
    /></span>
    <span />

    <UContainer class="relative max-w-302 max-md:px-4 pt-40 pb-26 lg:pt-45 lg:pb-30 xl:pt-62 xl:pb-53">
      <span class="max-lg:hidden h-[40%] absolute -top-[32px] right-[22.2%] z-3"><NuxtImg
        src="/images/finance-index/banner-vector-line1.svg"
        alt="img"
        class="h-full max-w-full align-middle"
      /></span>
      <span class="max-lg:hidden h-[70%] absolute bottom-[3px] right-[31%] z-0"><NuxtImg
        src="/images/finance-index/banner-vector-line2.svg"
        alt="img"
        class="h-full max-w-full align-middle"
      /></span>
      <div class="grid lg:grid-cols-2 items-center">
        <!-- Left Content -->
        <div class="">
          <h1 class="font-['Plus_Jakarta_Sans'] text-5xl lg:text-6xl font-bold text-white leading-tight lg:leading-[87.6px] mb-5">
            Financial Security Made
            <AnimatedWords :words="['Easier', 'Accountable', 'Unbeatable']" />
          </h1>

          <p class="text-white text-base lg:text-lg max-w-xl leading-[30px] font-medium mb-8 lg:mb-12">
            Staco is the dedicated platform for human management that helps to grow your startup
            business quickly
          </p>

          <div class="flex flex-wrap gap-4 lg:gap-6 items-center">
            <!-- Primary Button -->
            <OliveButton>Get Start For Free</OliveButton>

            <!-- Secondary "Let's talk" Button -->
            <button
              class="inline-flex group items-center gap-3 text-white font-medium text-base hover:text-[#44C486] transition-all ease-in duration-100 leading-[30px]"
            >
              <span>Let's talk</span>
              <span
                class="flex items-center justify-center w-[30px] h-[30px] group-hover:-rotate-45 group-hover:bg-[#44C486] group-hover:text-white transition-all ease-in duration-100 bg-white/10 rounded-[15px]"
              >
                <svg
                  width="16"
                  height="16"
                  viewBox="0 0 16 16"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M6 12L10 8L6 4"
                    stroke="white"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                </svg>
              </span>
            </button>
          </div>
        </div>

        <!-- Right Video -->
        <div class="flex justify-center lg:justify-end max-lg:mt-13">
          <HeroVideo />
        </div>
      </div>
    </UContainer>
  </section>
</template>
