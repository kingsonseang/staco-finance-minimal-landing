<script setup>
</script>

<template>
    <section class="py-20 bg-white">
        <UContainer>
            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <!-- Left: Text Content -->
                <div class="space-y-6">
                    <UBadge color="primary" variant="subtle" size="lg" class="bg-[#44C486]/10 text-[#44C486]">
                        Our Services
                    </UBadge>

                    <h2 class="text-4xl lg:text-5xl font-bold text-gray-900">
                        Manage team Increase productivity
                    </h2>

                    <p class="text-lg text-gray-600">
                        We denounce with righteous indignation and dislike men who are so beguiled and demoralized by
                        the charms of pleasure of the moment, so blinded by desire that they cannot foresee the pain and
                        trouble that are bound to ensue and equal blame.
                    </p>

                    <ul class="space-y-3">
                        <li class="flex items-start gap-3">
                            <UIcon name="i-heroicons-check-circle" class="w-6 h-6 text-[#44C486] flex-shrink-0 mt-1" />
                            <span class="text-gray-700">Temporibus autem quibusdam et aut officiis debitis</span>
                        </li>
                        <li class="flex items-start gap-3">
                            <UIcon name="i-heroicons-check-circle" class="w-6 h-6 text-[#44C486] flex-shrink-0 mt-1" />
                            <span class="text-gray-700">Lease ways this was through we a product</span>
                        </li>
                    </ul>

                    <UButton size="lg" class="bg-[#44C486] hover:bg-[#3AB377] text-white font-bold px-6 rounded-full">
                        Get Started
                    </UButton>
                </div>

                <!-- Right: Image -->
                <div class="relative">
                    <img src="https://placehold.co/600x400/1F2334/white?text=Team+Image" alt="Team collaboration"
                        class="rounded-2xl w-full">
                </div>
            </div>
        </UContainer>
    </section>
</template>
