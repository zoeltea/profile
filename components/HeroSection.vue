<template>
  <section ref="sectionRef" class="flex items-center py-16 md:py-24">
    <div class="max-w-7xl mx-auto px-4 w-full">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-start">
        <!-- Left Column - Software Engineer | Quality Assurance Engineer -->
        <div class="text-left relative">
          <h1 class="text-4xl md:text-6xl font-bold mb-6 text-white">
            Hi, I'm <span class="text-blue-400">Iyong</span>
          </h1>
          <h2 class="text-2xl md:text-4xl text-blue-400 mb-4">Software Engineer | Quality Assurance Engineer</h2>
          <p class="text-lg text-gray-300 mb-8">Passionate about creating innovative backend solutions with clean code and
            also antusias of quality Software.</p>
          <div class="flex flex-col sm:flex-row gap-8 mb-8">
            <div>
              <div class="text-3xl md:text-4xl font-bold text-blue-400 mb-2">9+</div>
              <div class="text-gray-300">Years Experience</div>
            </div>
          </div>
          <div class="mt-16 text-center">
            <a href="#about"
              class="text-gray-400 hover:text-blue-400 transition-colors flex flex-col items-center animate-bounce"
              aria-label="Scroll down to About section">
              <i class="fas fa-chevron-down text-xl" aria-hidden="true"></i>
            </a>
          </div>
        </div>

        <!-- Right Column -->
        <div class="space-y-12">
          <!-- About Me Section -->
          <div class="pb-12 border-b border-[#252525]">
            <div class="flex justify-between items-center mb-4">
              <h3 class="text-2xl font-bold text-white">About Me</h3>
              <a href="#about" class="text-blue-400 hover:text-blue-300 transition-colors text-sm"
                aria-label="Learn more about me">Learn More →</a>
            </div>
            <p class="text-gray-300 text-lg leading-relaxed">
              I specialize in creating functional backend and quality software.
              With expertise in modern web technologies.
            </p>
          </div>

          <!-- My Work Section -->
          <div class="pb-12 border-b border-[#252525]">
            <div class="flex justify-between items-center mb-4">
              <h3 class="text-2xl font-bold text-white">Featured Work</h3>
              <a href="#portfolio" class="text-blue-400 hover:text-blue-300 transition-colors text-sm"
                aria-label="Browse my portfolio">Browse Portfolio
                →</a>
            </div>
            <div class="space-y-6">
              <!-- <img src="https://placehold.co/600x400" alt="Featured Project" class="w-full rounded-lg"> -->
              <p class="text-gray-300 text-lg">

              </p>
            </div>
          </div>

          <!-- Social Links -->
          <div class="flex items-center gap-6">
            <h3 class="text-white font-medium">Connect:</h3>
            <div class="flex gap-4">
              <a href="https://github.com/zoeltea" target="_blank"
                class="text-gray-300 hover:text-blue-400 transition-colors" aria-label="Visit my GitHub profile">
                <i class="fab fa-github text-2xl" aria-hidden="true"></i>
              </a>
              <a href="https://www.linkedin.com/in/zul-yatman-442787100" target="_blank"
                class="text-gray-300 hover:text-blue-400 transition-colors" aria-label="Connect with me on LinkedIn">
                <i class="fab fa-linkedin text-2xl" aria-hidden="true"></i>
              </a>
              <a href="mailto:zoeltea@gmail.com" class="text-gray-300 hover:text-blue-400 transition-colors"
                aria-label="Send me an email">
                <i class="fas fa-envelope text-2xl" aria-hidden="true"></i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const sectionRef = ref(null)

onMounted(() => {
  // For hero section, we make it visible immediately
  if (sectionRef.value) {
    sectionRef.value.style.opacity = '1'
  }
})
</script>
