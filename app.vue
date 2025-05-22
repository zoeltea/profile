<template>
  <div class="min-h-screen bg-[#121212] relative">
    <Navigation />
    <HeroSection />
    <div class="bg-[#1a1a1a]">
      <AboutSection />
      <SkillsSection />
      <PortfolioSection :projects="projects" @open-modal="openModal" />
    </div>
    <ContactSection />
    <ProjectModal v-if="isModalOpen" :project="selectedProject" @close="closeModal" />
    <FooterSection />
  </div>
</template>

<script setup>
import Navigation from './components/Navigation.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import PortfolioSection from './components/PortfolioSection.vue'
import ContactSection from './components/ContactSection.vue'
import ProjectModal from './components/ProjectModal.vue'
import SkillsSection from './components/SkillsSection.vue'
import FooterSection from './components/FooterSection.vue'

const selectedProject = ref(null)
const isModalOpen = ref(false)
const projects = ref()

const openModal = (project) => {
  selectedProject.value = project
  isModalOpen.value = true
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  isModalOpen.value = false
  document.body.style.overflow = ''
  selectedProject.value = null
}

// Clean up any lingering modal state if component is unmounted
onUnmounted(() => {
  if (document.body.style.overflow === 'hidden') {
    document.body.style.overflow = ''
  }
  selectedProject.value = null
  isModalOpen.value = false
})

useHead({
  title: 'Zul Yatman - Software Engineer | Quality Assurance Engineer',
  meta: [
    {
      name: 'description',
      content: 'Hallo, my name is zul.
I start career as IT support at gas and oil drilling services company for 4 years then to be java developer for 3 months. I received offering for Test engineer and Software Engineer. I already working as Test engineer and today as Software Engineer.
My experiences Test engineer in Wirecard, BBM messanger, Vidio.com, Bukalapak and Software Engineer in Bukalapak.
As Test engineer then Software Engineer with 9 Years of Experience specializing in Golang, Ruby, PHP - Ready to Accelerate Innovation in Your Team'
    },
    // Open Graph
    {
      property: 'og:title',
      content: 'Zul Yatman - Software Engineer | Quality Assurance Engineer'
    },
    {
      property: 'og:description',
      content: 'Software Engineer | Quality Assurance Engineer with over 9 years of experience specializing in Vue.js, React, and full-stack development.'
    },
    {
      property: 'og:type',
      content: 'website'
    },
    // Twitter Card
    {
      name: 'twitter:card',
      content: 'summary'
    },
    {
      name: 'twitter:title',
      content: 'Zul Yatman - Software Engineer | Quality Assurance Engineer'
    },
    {
      name: 'twitter:description',
      content: 'Software Engineer | Quality Assurance Engineer with over 9 years of experience specializing in Vue.js, React, and full-stack development.'
    }
  ],
  htmlAttrs: {
    lang: 'en'
  },
  link: [
    {
      rel: 'preconnect',
      href: 'https://cdnjs.cloudflare.com'
    },
    {
      rel: 'preload',
      href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css',
      as: 'style',
      onload: "this.onload=null;this.rel='stylesheet'"
    },
    // Fallback for browsers that don't support onload on link
    {
      rel: 'stylesheet',
      href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css',
      media: 'print',
      onload: "this.media='all'"
    },
    {
      rel: 'preconnect',
      href: 'https://fonts.googleapis.com'
    },
    {
      rel: 'preconnect',
      href: 'https://fonts.gstatic.com',
      crossorigin: 'anonymous'
    },
    {
      rel: 'preload',
      href: 'https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&display=swap',
      as: 'style',
      onload: "this.onload=null;this.rel='stylesheet'"
    },
    // Fallback for browsers that don't support onload on link
    {
      rel: 'stylesheet',
      href: 'https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&display=swap',
      media: 'print',
      onload: "this.media='all'"
    }
  ]
})
</script>

<style>
html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Space Grotesk', sans-serif;
}
</style>
