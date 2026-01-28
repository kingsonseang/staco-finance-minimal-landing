<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-white dark:from-gray-950 dark:to-gray-900">
    <!-- Hero Section -->
    <section class="relative overflow-hidden">
      <div
        class="absolute inset-0 bg-gradient-to-br from-primary-100/20 via-transparent to-primary-50/10 dark:from-primary-950/20 dark:to-transparent" />
      <UContainer class="relative py-24 sm:py-32">
        <div class="mx-auto max-w-4xl text-center">
          <UBadge color="primary" variant="subtle" size="lg" class="mb-6">
            Smart Finance Platform
          </UBadge>
          <h1 class="text-5xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-6xl lg:text-7xl mb-6">
            Smart Financial Solutions for
            <span class="text-primary-500 dark:text-primary-400">Modern Businesses</span>
          </h1>
          <p class="text-xl text-gray-600 dark:text-gray-400 mb-10 max-w-2xl mx-auto">
            Empower your business with intelligent finance management, real-time analytics, and seamless payment
            processing.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <UButton size="xl" color="primary" trailing-icon="i-lucide-arrow-right">
              Get Started Free
            </UButton>
            <UButton size="xl" color="neutral" variant="outline" icon="i-lucide-calendar">
              Schedule Demo
            </UButton>
          </div>
        </div>
      </UContainer>
    </section>

    <!-- Services Section -->
    <section class="py-24 sm:py-32">
      <UContainer>
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-5xl mb-4">
            Everything You Need to Manage Your Finances
          </h2>
          <p class="text-xl text-gray-600 dark:text-gray-400 max-w-2xl mx-auto">
            Powerful tools designed to streamline your financial operations
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <UCard v-for="service in services" :key="service.title"
            class="hover:shadow-xl transition-shadow duration-300">
            <template #header>
              <div class="flex items-center gap-4">
                <div class="p-3 rounded-lg bg-primary-100 dark:bg-primary-950">
                  <UIcon :name="service.icon" class="w-6 h-6 text-primary-600 dark:text-primary-400" />
                </div>
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                  {{ service.title }}
                </h3>
              </div>
            </template>
            <p class="text-gray-600 dark:text-gray-400">
              {{ service.description }}
            </p>
          </UCard>
        </div>
      </UContainer>
    </section>

    <!-- Pricing Section -->
    <section class="py-24 sm:py-32 bg-gray-50 dark:bg-gray-900/50">
      <UContainer>
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-5xl mb-4">
            Simple, Transparent Pricing
          </h2>
          <p class="text-xl text-gray-600 dark:text-gray-400">
            Choose the plan that fits your business needs
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-7xl mx-auto">
          <UPricingCard v-for="plan in pricing" :key="plan.name" :title="plan.name" :description="plan.description"
            :price="plan.price" :cycle="plan.period" :features="plan.features" :highlight="plan.highlighted" :button="{
              label: plan.cta,
              color: plan.highlighted ? 'primary' : 'neutral',
              variant: plan.highlighted ? 'solid' : 'outline'
            }" orientation="vertical" class="hover:scale-105 transition-transform duration-300"
            :class="{ 'ring-2 ring-primary-500 dark:ring-primary-400': plan.highlighted }" />
        </div>
      </UContainer>
    </section>

    <!-- Testimonials Section -->
    <section class="py-24 sm:py-32">
      <UContainer>
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-5xl mb-4">
            Trusted by Thousands of Businesses
          </h2>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <UCard v-for="testimonial in testimonials" :key="testimonial.author"
            class="hover:shadow-xl transition-shadow duration-300">
            <div class="flex flex-col gap-4">
              <UIcon name="i-lucide-quote" class="w-10 h-10 text-primary-500 dark:text-primary-400" />
              <p class="text-gray-700 dark:text-gray-300 italic">
                "{{ testimonial.quote }}"
              </p>
              <div class="flex items-center gap-3 mt-4">
                <UAvatar :alt="testimonial.author" size="md" class="bg-primary-500">
                  {{ testimonial.avatar }}
                </UAvatar>
                <div>
                  <p class="font-semibold text-gray-900 dark:text-white">
                    {{ testimonial.author }}
                  </p>
                  <p class="text-sm text-gray-600 dark:text-gray-400">
                    {{ testimonial.role }}
                  </p>
                </div>
              </div>
            </div>
          </UCard>
        </div>
      </UContainer>
    </section>

    <!-- FAQ Section -->
    <section class="py-24 sm:py-32 bg-gray-50 dark:bg-gray-900/50">
      <UContainer>
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-5xl mb-4">
            Frequently Asked Questions
          </h2>
        </div>

        <div class="max-w-3xl mx-auto">
          <UAccordion :items="faqItems" :ui="{
            item: 'py-4'
          }" />
        </div>
      </UContainer>
    </section>

    <!-- CTA Section -->
    <section class="py-24 sm:py-32">
      <UContainer>
        <UCard class="bg-gradient-to-r from-primary-500 to-primary-600 dark:from-primary-600 dark:to-primary-700">
          <div class="text-center py-12">
            <h2 class="text-4xl font-bold text-white mb-4">
              Ready to Transform Your Finance Management?
            </h2>
            <p class="text-xl text-primary-50 mb-8 max-w-2xl mx-auto">
              Join thousands of businesses already using our platform to streamline their financial operations.
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
              <UButton size="xl" trailing-icon="i-lucide-arrow-right">
                Start Free Trial
              </UButton>
              <UButton size="xl" variant="outline" class="text-white border-white hover:bg-white/10">
                Contact Sales
              </UButton>
            </div>
          </div>
        </UCard>
      </UContainer>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 dark:bg-gray-950 text-gray-300">
      <UContainer class="py-16">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
          <div class="col-span-1 md:col-span-1">
            <div class="flex items-center gap-2 mb-4">
              <UIcon name="i-lucide-wallet" class="w-8 h-8 text-primary-500" />
              <span class="text-2xl font-bold text-white">FinanceApp</span>
            </div>
            <p class="text-gray-400">
              Smart financial solutions for modern businesses
            </p>
          </div>

          <div>
            <h3 class="text-white font-semibold mb-4">Product</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-primary-400 transition-colors">Features</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Pricing</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Security</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Integrations</a></li>
            </ul>
          </div>

          <div>
            <h3 class="text-white font-semibold mb-4">Company</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-primary-400 transition-colors">About Us</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Careers</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Blog</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Contact</a></li>
            </ul>
          </div>

          <div>
            <h3 class="text-white font-semibold mb-4">Legal</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-primary-400 transition-colors">Privacy Policy</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Terms of Service</a></li>
              <li><a href="#" class="hover:text-primary-400 transition-colors">Cookie Policy</a></li>
            </ul>
          </div>
        </div>

        <div class="pt-8 border-t border-gray-800 flex flex-col sm:flex-row justify-between items-center gap-4">
          <p class="text-gray-400 text-sm">
            © 2026 FinanceApp. All rights reserved.
          </p>
          <div class="flex gap-4">
            <a href="#" class="text-gray-400 hover:text-primary-400 transition-colors">
              <UIcon name="i-lucide-twitter" class="w-5 h-5" />
            </a>
            <a href="#" class="text-gray-400 hover:text-primary-400 transition-colors">
              <UIcon name="i-lucide-linkedin" class="w-5 h-5" />
            </a>
            <a href="#" class="text-gray-400 hover:text-primary-400 transition-colors">
              <UIcon name="i-lucide-github" class="w-5 h-5" />
            </a>
          </div>
        </div>
      </UContainer>
    </footer>
  </div>
</template>

<script setup lang="ts">
const services = [
  {
    icon: 'i-lucide-shield-check',
    title: 'Secure Payments',
    description: 'Process payments safely with bank-grade encryption and fraud detection'
  },
  {
    icon: 'i-lucide-bar-chart-3',
    title: 'Real-time Analytics',
    description: 'Get instant insights into your financial performance with live dashboards'
  },
  {
    icon: 'i-lucide-file-text',
    title: 'Automated Invoicing',
    description: 'Create and send professional invoices automatically on your schedule'
  },
  {
    icon: 'i-lucide-globe',
    title: 'Multi-Currency Support',
    description: 'Accept payments in 150+ currencies with automatic conversion'
  },
  {
    icon: 'i-lucide-trending-up',
    title: 'Financial Reports',
    description: 'Generate comprehensive reports for taxes, compliance, and planning'
  },
  {
    icon: 'i-lucide-headphones',
    title: '24/7 Support',
    description: 'Get help anytime from our dedicated finance experts'
  }
]

const pricing = [
  {
    name: 'Starter',
    price: '$29',
    period: '/month',
    description: 'Perfect for small businesses just getting started',
    features: [
      'Up to 100 transactions/month',
      'Basic analytics dashboard',
      'Email support',
      '1 user account',
      'Standard security'
    ],
    cta: 'Start Free Trial',
    highlighted: false
  },
  {
    name: 'Professional',
    price: '$99',
    period: '/month',
    description: 'For growing businesses that need more power',
    features: [
      'Unlimited transactions',
      'Advanced analytics & reports',
      'Priority support',
      '5 user accounts',
      'Advanced security',
      'API access',
      'Custom integrations'
    ],
    cta: 'Get Started',
    highlighted: true
  },
  {
    name: 'Enterprise',
    price: 'Custom',
    period: 'contact us',
    description: 'Tailored solutions for large organizations',
    features: [
      'Everything in Professional',
      'Unlimited user accounts',
      'Dedicated account manager',
      'Custom development',
      'SLA guarantee',
      'White-label options'
    ],
    cta: 'Contact Sales',
    highlighted: false
  }
]

const testimonials = [
  {
    quote: 'This platform transformed how we handle finances. The automation saved us 20 hours per week!',
    author: 'Sarah Johnson',
    role: 'CFO, TechStart Inc.',
    avatar: 'SJ'
  },
  {
    quote: 'The real-time analytics gave us insights we never had before. Game changer for our cash flow management.',
    author: 'Michael Chen',
    role: 'Founder, GrowthLabs',
    avatar: 'MC'
  },
  {
    quote: 'Exceptional support team and the most intuitive financial software we\'ve used. Highly recommend!',
    author: 'Emily Rodriguez',
    role: 'Finance Director, Innovate Co.',
    avatar: 'ER'
  }
]

const faqItems = [
  {
    label: 'How secure is your platform?',
    content: 'We use bank-grade 256-bit encryption, are PCI DSS compliant, and undergo regular third-party security audits. Your financial data is stored in secure, redundant data centers with 24/7 monitoring.'
  },
  {
    label: 'Can I switch plans anytime?',
    content: 'Yes! You can upgrade or downgrade your plan at any time. Changes take effect immediately, and we\'ll prorate any charges or credits automatically.'
  },
  {
    label: 'What payment methods do you accept?',
    content: 'We accept all major credit cards (Visa, Mastercard, Amex), bank transfers, and digital wallets. For Enterprise plans, we can arrange custom payment terms.'
  },
  {
    label: 'Is there a free trial?',
    content: 'Yes, we offer a 14-day free trial with full access to all Professional features. No credit card required to start.'
  },
  {
    label: 'Do you offer refunds?',
    content: 'We offer a 30-day money-back guarantee. If you\'re not satisfied for any reason, contact us within 30 days for a full refund.'
  }
]
</script>
