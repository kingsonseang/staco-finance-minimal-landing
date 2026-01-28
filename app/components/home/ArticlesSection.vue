<script setup>
const articles = [
    {
        title: 'We always try to discover new ideas that lead world',
        excerpt: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form',
        author: 'Asa Smith',
        date: '16 hours ago',
        image: 'https://placehold.co/400x300/1F2334/white?text=Article+1',
        bgColor: 'bg-white'
    },
    {
        title: 'Looking over stars in the distance',
        excerpt: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration',
        author: 'John Doe',
        date: '2 days ago',
        image: 'https://placehold.co/400x300/004D42/white?text=Article+2',
        bgColor: 'bg-[#004D42]'
    },
    {
        title: 'Convenient way to any financial business brand',
        excerpt: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered',
        author: 'Jane Smith',
        date: '1 week ago',
        image: 'https://placehold.co/400x300/B2EDA1/1F2334?text=Article+3',
        bgColor: 'bg-[#B2EDA1]'
    }
]
</script>

<template>
    <section class="py-20 bg-white">
        <UContainer>
            <div class="mb-12">
                <UBadge color="primary" variant="subtle" size="lg" class="bg-[#44C486]/10 text-[#44C486]">
                    Resource
                </UBadge>
                <h2 class="text-4xl lg:text-5xl font-bold text-gray-900 mt-4">
                    Latest Articles
                </h2>
            </div>

            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <UCard v-for="(article, index) in articles" :key="index" :ui="{
                    base: `${article.bgColor} ${article.bgColor === 'bg-white' ? 'border border-gray-200' : ''} overflow-hidden`,
                    body: 'space-y-4'
                }">
                    <img :src="article.image" :alt="article.title" class="w-full h-48 object-cover rounded-lg">

                    <h3 :class="[
                        'text-xl font-bold leading-tight',
                        article.bgColor === 'bg-white' ? 'text-gray-900' : 'text-white'
                    ]">
                        {{ article.title }}
                    </h3>

                    <p :class="[
                        'text-sm leading-relaxed',
                        article.bgColor === 'bg-white' ? 'text-gray-600' : 'text-white/80'
                    ]">
                        {{ article.excerpt }}
                    </p>

                    <div class="flex items-center gap-3 pt-2">
                        <UAvatar size="sm" :alt="article.author" />
                        <div>
                            <p :class="[
                                'text-sm font-medium',
                                article.bgColor === 'bg-white' ? 'text-gray-900' : 'text-white'
                            ]">
                                {{ article.author }}
                            </p>
                            <p :class="[
                                'text-xs',
                                article.bgColor === 'bg-white' ? 'text-gray-500' : 'text-white/60'
                            ]">
                                {{ article.date }}
                            </p>
                        </div>
                    </div>
                </UCard>
            </div>
        </UContainer>
    </section>
</template>
