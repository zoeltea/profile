<template>
  <footer ref="sectionRef"
    class="bg-[#121212] py-16 relative overflow-hidden opacity-0 translate-y-10 transition-all duration-700 ease-out">
    <!-- Background Accent -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[800px] h-[800px] opacity-20">
        <div
          class="w-full h-full rounded-full bg-gradient-to-br from-blue-500/30 via-purple-500/30 to-pink-500/30 blur-3xl">
        </div>
      </div>
    </div>
    <!-- Content -->
    <div class="max-w-6xl mx-auto px-4 relative z-10">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-12 mb-12">
        <!-- Logo & Description -->
        <div class="col-span-2">
          <h3 class="text-2xl font-bold text-white mb-4">Iyong</h3>
          <p class="text-gray-400 mb-6 max-w-md">
            Software Developer specializing in building exceptional digital experiences that make people's lives
            simpler.
          </p>
          <div class="flex gap-4">
            <a href="https://github.com/Iyongbudiarso/" target="_blank"
              class="text-gray-400 hover:text-white transition-colors" aria-label="Visit my GitHub profile">
              <i class="fab fa-github text-2xl" aria-hidden="true"></i>
              <span class="sr-only">GitHub</span>
            </a>
            <a href="https://www.linkedin.com/in/iyongbudiarso/" target="_blank"
              class="text-gray-400 hover:text-white transition-colors" aria-label="Visit my LinkedIn profile">
              <i class="fab fa-linkedin text-2xl" aria-hidden="true"></i>
              <span class="sr-only">LinkedIn</span>
            </a>
            <a href="mailto:iyongbudiarso@gmail.com" class="text-gray-400 hover:text-white transition-colors"
              aria-label="Send me an email">
              <i class="fas fa-envelope text-2xl" aria-hidden="true"></i>
              <span class="sr-only">Email</span>
            </a>
          </div>
        </div>

        <!-- Navigation -->
        <div>
          <h4 class="text-lg font-semibold text-white mb-4">Quick Links</h4>
          <nav class="flex flex-col gap-3">
            <a href="#" class="text-gray-400 hover:text-white transition-colors"
              aria-label="Go to home section">Home</a>
            <a href="#about" class="text-gray-400 hover:text-white transition-colors"
              aria-label="Go to about section">About</a>
            <a href="#portfolio" class="text-gray-400 hover:text-white transition-colors"
              aria-label="Go to portfolio section">Portfolio</a>
            <a href="#contact" class="text-gray-400 hover:text-white transition-colors"
              aria-label="Go to contact section">Contact</a>
          </nav>
        </div>
      </div>

      <!-- Copyright -->
      <div class="pt-8 border-t border-[#252525] text-center">
        <p class="text-gray-400">© {{ new Date().getFullYear() }} Iyong. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const sectionRef = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        sectionRef.value.classList.remove('opacity-0', 'translate-y-10')
        observer.unobserve(entry.target)
      }
    },
    {
      threshold: 0.1
    }
  )

  if (sectionRef.value) {
    observer.observe(sectionRef.value)
  }
})
</script>
