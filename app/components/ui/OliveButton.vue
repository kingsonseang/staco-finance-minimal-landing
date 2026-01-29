<script setup lang="ts">
interface Props {
  to?: string
  onClick?: () => void
}

const props = defineProps<Props>()

// Determine if this should be a link or button
const isLink = computed(() => !!props.to)
const component = computed(() => isLink.value ? 'NuxtLink' : 'button')
</script>

<template>
  <component
    :is="component"
    :to="to"
    class="w-[220px] h-[60px] bg-[#44C486] rounded-full flex items-center justify-center capitalize text-white relative overflow-hidden transition-all duration-300 font-bold border-0 cursor-pointer no-underline hover:bg-[#B2EDA1] focus:bg-[#B2EDA1] group"
    @click="onClick"
  >
    <span class="btn-inner inline-block transition-transform duration-800 ease-[cubic-bezier(0.15,0.85,0.31,1)] group-hover:-translate-y-[150%] max-md:text-sm">
      <span class="btn-normal-text relative z-11 text-white transition-opacity duration-600 ease-[cubic-bezier(0.15,0.85,0.31,1)] group-hover:opacity-0 group-hover:text-[#111111]">
        <slot />
      </span>
      <span class="btn-hover-text inline-block absolute w-full top-1/2 left-1/2 -translate-x-1/2 translate-y-[80%] opacity-0 z-11 text-white transition-all duration-600 ease-[cubic-bezier(0.15,0.85,0.31,1)] group-hover:translate-y-full group-hover:opacity-100 group-hover:text-[#111111]">
        <slot />
      </span>
    </span>
  </component>
</template>
