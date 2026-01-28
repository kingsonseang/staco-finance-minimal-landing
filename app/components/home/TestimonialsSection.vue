<script setup>
const testimonial = {
    quote: 'I must explain to you how all this mistaken. Idea of denouncing pleasure praising pain was born and will give you complete account of the system and expound',
    author: 'Asa Smith',
    role: 'CEO, Staco Marketing'
}

const companies = [
    { name: 'Company 1', logo: 'i-simple-icons-google' },
    { name: 'Company 2', logo: 'i-simple-icons-microsoft' },
    { name: 'Company 3', logo: 'i-simple-icons-apple' },
    { name: 'Company 4', logo: 'i-simple-icons-amazon' },
    { name: 'Company 5', logo: 'i-simple-icons-meta' }
]
</script>

<template>
    <section class="py-20 bg-gray-50">
        <UContainer>
            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <!-- Left: Profile Image -->
                <div class="relative">
                    <div class="w-64 h-64 mx-auto lg:mx-0 rounded-full bg-[#44C486]/20 overflow-hidden">
                        <img src="https://placehold.co/400x400/44C486/white?text=Profile" alt="Testimonial author"
                            class="w-full h-full object-cover">
                    </div>
                    <!-- Decorative element -->
                    <div class="absolute -bottom-4 -right-4 w-32 h-32 bg-[#1F2334] rounded-tl-[80px]" />
                </div>

                <!-- Right: Testimonial -->
                <div class="space-y-6">
                    <UIcon name="i-heroicons-chat-bubble-left-right" class="w-12 h-12 text-[#44C486]" />

                    <blockquote class="text-xl lg:text-2xl text-gray-700 leading-relaxed">
                        "{{ testimonial.quote }}"
                    </blockquote>

                    <div>
                        <p class="font-bold text-lg text-gray-900">{{ testimonial.author }}</p>
                        <p class="text-gray-600">{{ testimonial.role }}</p>
                    </div>

                    <!-- Company Logos -->
                    <div class="flex flex-wrap gap-8 pt-4">
                        <UIcon v-for="(company, index) in companies" :key="index" :name="company.logo"
                            class="w-8 h-8 text-gray-400 hover:text-gray-600 transition-colors" />
                    </div>
                </div>
            </div>
        </UContainer>
    </section>
</template>
