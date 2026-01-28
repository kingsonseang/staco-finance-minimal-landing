<script setup>
const heroData = {
    badge: 'New release',
    title: 'Financial Security Made Easier',
    description: 'Where their business solution for human resources, payroll and these a temporary administrative',
    primaryButton: {
        text: 'Get Started',
        link: '#'
    },
    secondaryButton: {
        text: 'Learn More',
        link: '#'
    }
}
</script>

<template>
    <section class="relative bg-[#1F2334] overflow-hidden">
        <!-- Decorative SVG curves -->
        <div class="absolute inset-0 pointer-events-none">
            <!-- Add decorative curved lines from Figma -->
        </div>

        <UContainer class="py-20 lg:py-32">
            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <!-- Left Content -->
                <div class="space-y-8">
                    <UBadge color="primary" variant="subtle" size="lg" class="bg-[#44C486]/10 text-[#44C486]">
                        {{ heroData.badge }}
                    </UBadge>

                    <h1 class="text-5xl lg:text-6xl font-bold text-white leading-tight">
                        {{ heroData.title }}
                    </h1>

                    <p class="text-lg text-gray-300 max-w-xl">
                        {{ heroData.description }}
                    </p>

                    <div class="flex flex-wrap gap-4">
                        <UButton :to="heroData.primaryButton.link" size="xl"
                            class="bg-[#44C486] hover:bg-[#3AB377] text-white font-bold px-8 py-4 rounded-full">
                            {{ heroData.primaryButton.text }}
                        </UButton>

                        <UButton :to="heroData.secondaryButton.link" size="xl" variant="outline"
                            class="border-2 border-white/20 text-white hover:bg-white/10 font-bold px-8 py-4 rounded-full">
                            {{ heroData.secondaryButton.text }}
                        </UButton>
                    </div>
                </div>

                <!-- Right Video -->
                <div class="flex justify-center lg:justify-end">
                    <HeroVideo />
                </div>
            </div>
        </UContainer>
    </section>
</template>
