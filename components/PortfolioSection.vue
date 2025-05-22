<template>
  <section ref="sectionRef" id="portfolio" class="py-16 opacity-0 translate-y-10 transition-all duration-700 ease-out">
    <div class="max-w-6xl mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-4xl font-bold text-white mb-4">My Portfolio</h2>
        <p class="text-gray-400 text-lg">Take a look at the latest projects I've done</p>
      </div>
      <div class="flex flex-col gap-12">
        <div v-for="(project, index) in projects" :key="index" @click="$emit('open-modal', project)"
          class="bg-[#121212] rounded-xl overflow-hidden shadow-xl transition-all duration-300 hover:shadow-2xl hover:shadow-white/5 cursor-pointer border border-[#252525] group"
          role="button" tabindex="0" :aria-label="`View details of ${project.title} project`"
          @keydown.enter="$emit('open-modal', project)">
          <div class="flex flex-col md:flex-row">
            <div class="md:w-1/2">
              <picture>
                <source :srcset="project.image.replace('.png', '.webp')" type="image/webp">
                <img :src="project.image" :alt="project.title" loading="lazy"
                  class="w-full h-full object-cover transition-transform duration-300 group-hover:scale-105">
              </picture>
            </div>
            <div class="md:w-1/2 p-8 md:p-12 flex flex-col justify-between">
              <div>
                <h3 class="text-2xl md:text-3xl font-bold mb-4 text-white">{{ project.title }}</h3>
                <p class="text-gray-300 mb-6 text-lg">{{ project.description }}</p>
                <div class="flex flex-wrap gap-2 mb-6">
                  <span v-for="tech in project.technologies" :key="tech"
                    class="px-4 py-2 bg-[#252525] text-sm font-medium text-gray-300 rounded-full border border-[#333333]">
                    {{ tech }}
                  </span>
                </div>
              </div>
              <div class="flex items-center text-gray-400 group-hover:text-white transition-colors">
                <span class="mr-2" aria-label="View details for {{ project.title }}">View Project</span>
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                  <path fill-rule="evenodd"
                    d="M12.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-2.293-2.293a1 1 0 010-1.414z"
                    clip-rule="evenodd" />
                </svg>
              </div>
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

defineProps({
  projects: {
    type: Array,
    required: true
  }
})

defineEmits(['open-modal'])

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
