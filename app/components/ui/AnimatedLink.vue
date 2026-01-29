<script setup lang="ts">
interface Props {
  to: string
}

defineProps<Props>()
</script>

<template>
  <NuxtLink
    :to="to"
    class="text-white/70 hover:text-white transition-colors inline-block relative overflow-hidden group"
  >
    <span class="inline-block transition-transform duration-700 ease-[cubic-bezier(0.15,0.85,0.31,1)] group-hover:-translate-y-[150%]">
      <span class="relative z-10 transition-opacity duration-500 ease-[cubic-bezier(0.15,0.85,0.31,1)] group-hover:opacity-0">
        <slot />
      </span>
      <span class="inline-block absolute w-full top-1/2 left-1/2 -translate-x-1/2 translate-y-[80%] opacity-0 z-10 transition-all duration-500 ease-[cubic-bezier(0.15,0.85,0.31,1)] group-hover:translate-y-full group-hover:opacity-100">
        <slot />
      </span>
    </span>
  </NuxtLink>
</template>
