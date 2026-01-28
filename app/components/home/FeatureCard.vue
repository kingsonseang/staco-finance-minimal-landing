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
        base: 'bg-gray-50 dark:bg-gray-800 group',
        body: 'space-y-4',
        footer: 'flex items-center justify-between'
    }">
        <template #header>
            <div class="w-12 h-12 rounded-xl bg-green-100 dark:bg-green-900/30 flex items-center justify-center">
                <UIcon :name="icon" class="w-6 h-6 text-green-600 dark:text-green-500" />
            </div>
        </template>

        <div class="space-y-3">
            <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                {{ title }}
            </h3>
            <p class="text-gray-600 dark:text-gray-400 leading-relaxed">
                {{ description }}
            </p>
        </div>

        <template #footer>
            <NuxtLink :to="link || '#'"
                class="text-green-600 dark:text-green-500 font-medium hover:text-green-700 dark:hover:text-green-400 transition-colors">
                Learn more
            </NuxtLink>

            <UButton icon="i-heroicons-arrow-up-right" color="primary" variant="solid" size="sm"
                :ui="{ rounded: 'rounded-full' }"
                class="bg-green-500 hover:bg-green-600 dark:bg-green-600 dark:hover:bg-green-700 " :to="link" :ui="{
                    icon: 'group-hover:rotate-[45deg]'
                }" />
        </template>
    </UCard>
</template>