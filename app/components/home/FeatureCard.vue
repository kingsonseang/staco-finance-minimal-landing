<script setup>
defineProps({
    icon: {
        type: String,
        required: true
    },
    title: {
        type: String,
        required: true
    },
    description: {
        type: String,
        required: true
    },
    link: {
        type: String,
        default: '#'
    }
})
</script>

<template>
    <UCard :ui="{
        base: 'bg-[#E8E8E8] dark:bg-gray-800 group',
        body: 'space-y-4 p-6',
        footer: 'flex items-center justify-between px-6 pb-6',
        rounded: 'rounded-3xl'
    }">
        <template #header>
            <div class="w-14 h-14 rounded-2xl bg-[#004D42] flex items-center justify-center">
                <UIcon :name="icon" class="w-7 h-7 text-white" />
            </div>
        </template>

        <div class="space-y-3">
            <h3 class="text-lg font-bold text-[#000000] dark:text-white"
                style="font-family: 'Plus Jakarta Sans', sans-serif;">
                {{ title }}
            </h3>
            <p class="text-base text-[#444444] dark:text-gray-400 leading-[30px] font-medium"
                style="font-family: 'DM Sans', sans-serif;">
                {{ description }}
            </p>
        </div>

        <template #footer>
            <NuxtLink :to="link || '#'"
                class="text-base text-[#444444] dark:text-gray-300 font-bold hover:text-gray-900 dark:hover:text-white transition-colors"
                style="font-family: 'DM Sans', sans-serif;">
                Learn more
            </NuxtLink>

            <UButton icon="i-heroicons-arrow-right" size="md" color="white" variant="solid" :ui="{
                rounded: 'rounded-full',
                padding: { md: 'p-2.5' }
            }" class="w-10 h-10 bg-white text-gray-600 hover:bg-gray-100" :to="link" />
        </template>
    </UCard>
</template>