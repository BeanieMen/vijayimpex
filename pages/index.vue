<template>
  <div class="min-h-screen bg-white">
    <!-- Curtain Overlay -->
    <div ref="curtain" class="fixed inset-0 bg-[#556B2F] z-[100]"></div>

    <!-- Sticky Navigation -->
    <nav class="sticky top-0 shadow-md z-50 bg-[#d9d6b5] border-b border-[#556B2F]/10">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between h-16">
          <!-- Logo Section -->
          <div class="flex items-center space-x-4">
            <div class="flex-shrink-0">
              <img src="/logo.jpg" class="h-12 w-auto object-contain" alt="Vijay Impex Global Logo">
            </div>
            <nuxt-link to="/"
              class="text-xl md:text-2xl font-semibold text-black whitespace-nowrap hover:text-[#4A5A23] transition-colors">
              Vijay Impex Global
            </nuxt-link>
          </div>

          <!-- Navigation Links -->
          <div class="hidden md:flex items-center space-x-8">
            <nuxt-link v-for="(item, index) in navItems" :key="index" :to="`#${item.toLowerCase()}`"
              class="text-black hover:text-[#556B2F] transition-colors text-sm lg:text-base font-medium py-1.5 px-3 rounded-md hover:bg-[#f5f3d9]">
              {{ item }}
            </nuxt-link>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative bg-[#fffce4] flex items-center h-[90vh] max-h-[90vh]">
      <ClientOnly>
        <swiper-container ref="swiperContainer" slides-per-view="1" loop="true" autoplay-delay="10000"
          autoplay-disable-on-interaction="false" navigation="true" pagination="true" class="w-full h-full">

          <!-- First Slide -->
          <swiper-slide class="h-full flex items-center justify-center">
            <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 h-full flex items-center justify-center">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6 md:gap-8 items-center h-full">
                <!-- Image column -->
                <div class="relative h-full w-full flex items-center justify-center">
                  <img src="/indian-produce.png" alt="Indian Produce"
                    class="w-full h-auto max-h-[300px] sm:max-h-[350px] md:max-h-[400px] object-contain">
                </div>

                <!-- Content Column -->
                <div class="space-y-4 sm:space-y-6 py-4 sm:py-8 text-center flex flex-col items-center" id="hero-text">
                  <h1 class="text-2xl sm:text-3xl md:text-4xl font-bold text-[#556B2F]">
                    We Export A Wide Variety of Products
                  </h1>
                  <p class="text-sm sm:text-base md:text-lg text-gray-600">
                    From farm-fresh fruits and vegetables to authentic spices and dry fruits,
                    we deliver the finest Indian agricultural products to global markets.
                    Our diverse range meets international quality standards.
                  </p>
                  <button
                    class="bg-[#556B2F] text-white px-6 py-2 sm:px-8 sm:py-3 rounded-lg hover:bg-[#47582a] transition-colors duration-300 text-sm sm:text-base">
                    Export Now
                  </button>
                </div>
              </div>
            </div>
          </swiper-slide>

          <!-- Navigation Arrows -->
          <div class="swiper-button-prev"></div>
          <div class="swiper-button-next"></div>

          <!-- Pagination -->
          <div class="swiper-pagination"></div>
        </swiper-container>
      </ClientOnly>
    </section>

    <!-- Services Grid -->
    <section id="services" class="py-16 animate-on-scroll">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">Our Offerings</h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="(service, index) in services" :key="index"
            class="p-6 border rounded-xl hover:shadow-lg transition-shadow duration-300">
            <div class="h-16 w-16 bg-green-100 rounded-lg mb-4 flex items-center justify-center">
              <Icon :name="service.icon" class="w-8 h-8 text-green-700" />
            </div>
            <h3 class="text-xl font-semibold mb-2">{{ service.title }}</h3>
            <p class="text-gray-600">{{ service.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-16 bg-gray-50 animate-on-scroll">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row items-center gap-12">
        <div class="md:w-1/2">
          <p>place holder</p>
        </div>
        <div class="md:w-1/2">
          <h2 class="text-3xl font-bold mb-6">Globalizing Indian Produce</h2>
          <p class="text-gray-600 mb-6">
            We specialize in bridging the gap between premium Indian agricultural products and global markets.
            Our network of trusted farms and rigorous quality control ensures you receive the best of India's bounty.
          </p>
          <ul class="space-y-3">
            <li v-for="(item, index) in aboutPoints" :key="index" class="flex items-center">
              <Icon name="heroicons:check" class="w-5 h-5 text-green-700 mr-2" />
              {{ item }}
            </li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Certifications Section -->
    <section class="py-16 bg-white animate-on-scroll">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <h3 class="text-lg font-semibold text-gray-600 text-center mb-8">Certified & Approved By</h3>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 items-center">
          <img :data-src="cert" alt="Certification"
            class="h-20 object-contain opacity-75 hover:opacity-100 transition-opacity duration-300"
            v-for="(cert, index) in certifications" :key="index">
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        <div class="bg-[#373736] shadow-xl rounded-2xl p-8 sm:p-12 lg:p-16">
          <div class="max-w-4xl mx-auto text-center">
            <h2 class="text-3xl font-bold mb-12 text-[#fffce4]">Contact Details</h2>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
              <!-- Location Card -->
              <div class="space-y-4 p-6 rounded-xl bg-[#556B2F]/20 border border-[#556B2F]/30">
                <div class="flex justify-center">
                  <Icon name="heroicons:map-pin" class="w-8 h-8 text-[#fffce4]" />
                </div>
                <h3 class="text-lg font-semibold text-[#fffce4]">Our Location</h3>
                <p class="text-sm text-green-100/90">
                  E-36 OFFICE NO-307 2nd floor Jwahar park,
                  Laxmi Nagar-110091 Delhi India
                </p>
              </div>

              <!-- Phone Card -->
              <div class="space-y-4 p-6 rounded-xl bg-[#556B2F]/20 border border-[#556B2F]/30">
                <div class="flex justify-center">
                  <Icon name="heroicons:phone" class="w-8 h-8 text-[#fffce4]" />
                </div>
                <h3 class="text-lg font-semibold text-[#fffce4]">Phone</h3>
                <p class="text-sm text-green-100/90">
                  +971 58 524 8055<br>
                  +91-8929994562
                </p>
              </div>

              <!-- Email Card -->
              <div class="space-y-4 p-6 rounded-xl bg-[#556B2F]/20 border border-[#556B2F]/30">
                <div class="flex justify-center">
                  <Icon name="heroicons:envelope" class="w-8 h-8 text-[#fffce4]" />
                </div>
                <h3 class="text-lg font-semibold text-[#fffce4]">Our Email</h3>
                <p class="text-sm text-green-100/90 break-all">
                  vjayimpex.co@gmail.com
                </p>
              </div>
            </div>

            <!-- Additional Note -->
            <p class="mt-12 text-sm text-green-100/80 italic">
              Reach out to us for premium quality exports and partnership opportunities
            </p>
          </div>
        </div>
      </div>
    </section>
    <!-- Footer -->
    <footer class="bg-green-900 w-full text-white">
      <div class="mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Useful Links -->
          <div class="space-y-4">
            <h3 class="text-lg font-bold mb-4">Useful Links</h3>
            <ul class="space-y-2">
              <li v-for="(link, index) in usefulLinks" :key="index">
                <nuxt-link :to="link.path"
                  class="text-green-100 hover:text-green-300 transition-colors duration-300 text-sm">
                  {{ link.label }}
                </nuxt-link>
              </li>
            </ul>
          </div>

          <!-- About Section -->
          <div class="space-y-4 md:col-span-2">
            <h3 class="text-lg font-bold mb-4">About Us</h3>
            <p class="text-sm text-green-100">
              Vegetables & Indian fruits are some of the available assets that have proved the way getcally.
              Such action products are a truly demand across the good market.
            </p>
            <div class="flex gap-4 mt-6">
              <a v-for="(social, index) in socialLinks" :key="index" :href="social.url"
                class="text-green-100 hover:text-green-300 transition-colors duration-300">
                <Icon :name="social.icon" class="w-6 h-6" />
              </a>
            </div>
          </div>
        </div>

        <!-- Copyright -->
        <div class="border-t border-green-800 mt-8 pt-8 text-center">
          <p class="text-sm text-green-300">
            Copyright © 2014 vipm.yamac All rights reserved
          </p>
          <div class="mt-2 flex justify-center gap-4">
            <nuxt-link to="/terms" class="text-green-300 hover:text-green-100 transition-colors duration-300 text-sm">
              Terms of Service
            </nuxt-link>
            <nuxt-link to="/privacy" class="text-green-300 hover:text-green-100 transition-colors duration-300 text-sm">
              Privacy Policy
            </nuxt-link>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>
<script setup>
import { register } from 'swiper/element/bundle'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)
register()

const swiperContainer = ref(null)
const curtain = ref(null)
let currentAnimation = null

const navItems = ['About', 'Products', 'Services', 'Certifications', 'Contact']
const services = [
  {
    icon: 'mdi:fruit-pineapple',
    title: 'Seasonal Fruits',
    description: 'Export-quality fresh fruits harvested at peak seasonality'
  },
  {
    icon: 'mdi:leaf',
    title: 'Fresh Vegetables',
    description: 'Farm-to-table vegetables with optimal freshness control'
  },
  {
    icon: 'mdi:pepper',
    title: 'Spices & Dry Fruits',
    description: 'Authentic Indian spices and premium dry fruits collection'
  }
]

const usefulLinks = [
  { label: 'Home', path: '/' },
  { label: 'Products', path: '/products' },
  { label: 'About', path: '/about' },
  { label: 'Contact', path: '/contact' }
]

const socialLinks = [
  { icon: 'mdi:facebook', url: '#' },
  { icon: 'mdi:twitter', url: '#' },
  { icon: 'mdi:linkedin', url: '#' }
]

const aboutPoints = [
  '100% Organic Certified Produce',
  'Global Shipping & Logistics',
  'Food Safety Compliance',
  'Customized Packaging',
  '24/7 Quality Support'
]

const certifications = [
  '/certifications/fssai.png',
  '/certifications/usda.png',
  '/certifications/iso.png',
  '/certifications/halal.png'
]


const animateHeroText = (element) => {
  if (currentAnimation) currentAnimation.progress(1).kill()

  const children = gsap.utils.toArray(element.children)

  currentAnimation = gsap.timeline()
  currentAnimation.to(curtain.value, { opacity: 0, duration: 0.5 })

  children.forEach((child, i) => {
    currentAnimation.fromTo(child,
      { opacity: 0, y: 30 },
      {
        opacity: 1,
        y: 0,
        duration: 0.8,
        delay: i * 0.5, // Reduced delay multiplier
        ease: "power3.out"
      },
      i === 0 ? "+=0.1" : "<" // Reduced initial offset
    )
  })

  currentAnimation.eventCallback("onComplete", () => {
    currentAnimation = null
  })
}

const initScrollAnimations = () => {
  gsap.utils.toArray('.animate-on-scroll').forEach(element => {
    gsap.fromTo(element,
      { opacity: 0, y: 30 },
      {
        opacity: 1,
        y: 0,
        duration: 1,
        ease: "power2.out",
        scrollTrigger: {
          trigger: element,
          start: "top 80%",
          toggleActions: "play none none none",
        }
      }
    )
  })
}

onMounted(() => {
  gsap.fromTo(curtain.value,
    { y: '0%' },
    {
      y: '-100%',
      duration: 1.5,
      ease: "power3.inOut",
      onComplete: () => {
        const initSwiper = () => {
          if (swiperContainer.value?.swiper) {
            const swiper = swiperContainer.value.swiper

            // Initial animation
            animateHeroText(swiper.slides[0].querySelector('#hero-text'))

            // Handle slide changes
            swiper.on('slideChange', () => {
              const prevSlide = swiper.slides[swiper.previousIndex]
              gsap.set(prevSlide.querySelectorAll('#hero-text > *'), {
                opacity: 0,
                y: 30
              })

              const activeSlide = swiper.slides[swiper.activeIndex]
              animateHeroText(activeSlide.querySelector('#hero-text'))
            })

            swiper.autoplay.start()
          } else {
            setTimeout(initSwiper, 50)
          }
        }
        initSwiper()
        initScrollAnimations()
      }
    }
  )
})
</script>

<style>
#hero-text h1,
#hero-text p,
#hero-text button {
  opacity: 0;
  transform: translateY(30px);
}

.swiper-button-prev,
.swiper-button-next {
  @apply text-green-700 bg-white/80 backdrop-blur-sm p-4 rounded-full shadow-lg;
  --swiper-navigation-size: 24px;
  width: 48px;
  height: 48px;
}

.swiper-pagination-bullet {
  @apply bg-gray-400 opacity-100;
}

.swiper-pagination-bullet-active {
  @apply bg-green-700;
}

/* Curtain animation styles */
.curtain {
  transform-origin: top;
  will-change: transform;
}

.animate-on-scroll {
  opacity: 0;
  transform: translateY(20px);
}

img {
  transition: opacity 0.3s ease;
}

img:not([src]) {
  opacity: 0;
}

img[src] {
  opacity: 1;
}
</style>