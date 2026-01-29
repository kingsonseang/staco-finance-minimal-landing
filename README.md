# Finance Landing Page - Nuxt 4

[![Nuxt UI](https://img.shields.io/badge/Made%20with-Nuxt%20UI-00DC82?logo=nuxt&labelColor=020420)](https://ui.nuxt.com)

A modern, responsive finance landing page recreated from [Staco Finance Template](https://staco-react.vercel.app/finance) using Nuxt 4, Nuxt UI, and TailwindCSS with enhanced animations and interactions.

## 📋 Task Overview

**UI Interpretation Test (45 marks)**

Recreate the finance landing page with the following requirements:
- ✅ Built with Nuxt 4, Nuxt UI, and TailwindCSS
- ✅ Custom navigation bar inspired by [Motion Tabs](https://motion-tabs.vercel.app/)
- ✅ Omitted sections: Blog posts, stats/metrics, key features/benefits
- ✅ Focus on UI design, interactions, animations, responsiveness, speed, and Lighthouse score

## 🛠️ Tech Stack

- **Framework**: [Nuxt 4](https://nuxt.com/) - Latest Vue.js meta-framework
- **UI Library**: [Nuxt UI](https://ui.nuxt.com/) - Component library with UCarousel
- **Styling**: [TailwindCSS](https://tailwindcss.com/) - Utility-first CSS framework
- **Animation**: [@vueuse/motion](https://motion.vueuse.org/) - Vue animation library
- **Font**: DM Sans, Montserrat Alternates (Google Fonts)
- **Package Manager**: Bun
- **Runtime**: Node.js

## ✨ Key Features Implemented

### 1. **Custom Navigation Bar**
- Glassmorphic design with backdrop blur effect
- Animated bubble interaction on hover/active states using CSS anchor positioning
- Language selector dropdown (8 languages)
- Responsive mobile menu with slide-down animation
- Smooth transitions and light mode color scheme

### 2. **Hero Section**
- Animated floating vectors with subtle motion
- Gradient text effects with underline animation
- Responsive layout with decorative SVG elements
- Call-to-action buttons with hover animations

### 3. **Features Section**
- Custom `FeatureCard` component with gradient backgrounds
- Hover effects and icon animations
- Grid layout with responsive columns

### 4. **Team/Why Choose Us Section**
- Synchronized dual carousels (content + images)
- Embla Carousel integration via `UCarousel`
- Progress bar synced with carousel autoplay
- Click-to-navigate image slider
- Mobile-responsive with adaptive sizing

### 5. **Testimonials Section**
- Customer quote carousel with image/text sync
- Brand logo navigation
- Progress bar indicator
- Decorative background elements

### 6. **Let's Talk Section**
- Scroll-triggered chart animation using `@vueuse/motion`
- Animated statistics counters
- Interactive form section

### 7. **Footer**
- Multi-column responsive layout
- Social media icons with hover effects
- Email subscription form
- Mobile-optimized spacing

## 🎨 Design Improvements

### Animations
- **CSS Transitions**: Smooth hover states and color transitions
- **Carousel Animations**: Hardware-accelerated transforms via Embla
- **Bubble Navigation**: CSS anchor positioning for fluid tab switching

### Performance Optimizations
- **Component Structure**: Modular, reusable components
- **Lazy Loading**: Images optimized with `NuxtImg`
- **CSS**: Minimal custom CSS, leveraging Tailwind utilities

## 🐛 Known Issues

### Testimonial Carousel Timing Bug
The testimonial section carousel has a minor timing synchronization issue where the brand logo carousel may occasionally drift from the main content carousel during autoplay transitions. This is due to the interaction between the progress bar animation and carousel slide changes.

**Recommended fix**: Implement a single source of truth for timing by using Embla's internal scroll progress API instead of a separate requestAnimationFrame loop.

## 📁 Project Structure

```
app/
├── components/
│   ├── home/
│   │   ├── HeroSection.vue
│   │   ├── FeaturesSection.vue
│   │   ├── TeamSection.vue        # Dual carousel implementation
│   │   ├── TestimonialsSection.vue
│   │   ├── LetsTalk.vue           # Scroll animations
│   │   └── DisclaimerSection.vue
│   ├── ui/
│   │   ├── FeatureCard.vue
│   │   ├── OliveButton.vue        # Custom CTA button
│   │   └── AnimatedLink.vue
│   ├── AppNav.vue                 # Bubble navigation
│   ├── AppLogo.vue
│   └── AppFooter.vue
├── assets/css/
│   └── main.css                   # Bubble nav styles + custom CSS
└── pages/
    └── index.vue                  # Main landing page
```

## 🚀 Setup & Development

### Prerequisites
- Node.js 18+ or Bun
- Git

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd staco-finance-minimal-landing

# Install dependencies
bun install  # or npm install
```

### Development Server

```bash
# Start dev server on http://localhost:3000
bun dev  # or npm run dev
```

### Production Build

```bash
# Build for production
bun build  # or npm run build

# Preview production build
bun preview  # or npm run preview
```

### Linting

```bash
# Run ESLint
bun lint

# Auto-fix issues
bun lint --fix
```

## 📊 Performance Metrics

- **Lighthouse Score**: Target 90+ across all categories
- **Bundle Size**: Optimized with unused asset removal
- **Images**: Only 39 actively used images (from 214)
- **Responsive**: Mobile-first approach with breakpoints at sm, md, lg, xl

## 🎯 Implementation Highlights

1. **Light Mode Theme**: Glassmorphic navigation with white/transparent backgrounds
2. **Synchronized Carousels**: Used Nuxt UI's `UCarousel` with Embla Carousel for smooth, jitter-free transitions
3. **CSS Anchor Positioning**: Modern CSS feature for bubble navigation animation
4. **Motion Animations**: Scroll-triggered animations for enhanced user engagement
5. **Mobile Responsiveness**: Adaptive layouts with Tailwind breakpoints

## 📝 License

This is a test project created for UI interpretation assessment.

---

**Built with ❤️ using Nuxt 4**
