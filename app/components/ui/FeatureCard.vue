<script setup lang="ts">
interface Props {
  image: string
  title: string
  description: string
  link?: string
}

defineProps<Props>()
</script>

<template>
  <div class="bg-[#ECEFF1] p-[40px_30px] rounded-[30px] mb-[30px] transition-all duration-300 group">
    <!-- Icon -->
    <div class="mb-[31px]">
      <NuxtImg
        :src="image"
        alt="icon"
        class="w-auto h-auto max-w-full"
      />
    </div>

    <!-- Title -->
    <h5 class="font-['Montserrat_Alternates'] text-lg font-bold text-black mb-[19px] transition-all duration-500">
      {{ title }}
    </h5>

    <!-- Description -->
    <p class="mb-[70px] text-[#444444] leading-relaxed">
      {{ description }}
    </p>

    <!-- Link with Arrow -->
    <NuxtLink
      :to="link || '#'"
      class="flex items-center justify-between transition-all duration-700"
    >
      <span class="transition-all duration-500 text-[#444444] font-bold group-hover:text-[#44C486]">
        Learn more
      </span>

      <div class="h-10 w-10 rounded-full bg-black/10 flex items-center justify-center transition-all duration-300 group-hover:bg-[#44C486]">
        <div class="mb-[3px] ml-[2px]">
          <NuxtImg
            src="/images/icons/features-arrow-right.svg"
            alt="arrow"
            class="brightness-0 transition-all duration-300 group-hover:brightness-100 group-hover:rotate-[-45deg]"
          />
        </div>
      </div>
    </NuxtLink>
  </div>
</template>
