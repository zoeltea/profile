<template>
  <section ref="sectionRef" class="py-16 opacity-0 translate-y-10 transition-all duration-700 ease-out">
    <div class="max-w-6xl mx-auto px-4 relative overflow-hidden">
      <h2 class="text-3xl md:text-4xl font-bold text-center mb-12 text-white">Skills & Technologies</h2>

      <div class="relative">
        <!-- Navigation Arrows -->
        <button @click="prevSlide"
          class="absolute left-0 top-1/2 transform -translate-y-1/2 z-10 w-12 h-12 flex items-center justify-center bg-[#1a1a1a]/80 text-blue-400 hover:text-blue-300 transition-colors rounded-full"
          aria-label="View previous skills">
          <i class="fas fa-chevron-left text-2xl"></i>
        </button>

        <button @click="nextSlide"
          class="absolute right-0 top-1/2 transform -translate-y-1/2 z-10 w-12 h-12 flex items-center justify-center bg-[#1a1a1a]/80 text-blue-400 hover:text-blue-300 transition-colors rounded-full"
          aria-label="View next skills">
          <i class="fas fa-chevron-right text-2xl"></i>
        </button>

        <!-- Skills Carousel -->


        <!-- Dots Navigation -->
        <div class="flex justify-center mt-8 space-x-2">
          <button v-for="(_, index) in skillGroups" :key="index" @click="currentSlide = index"
            class="w-3 h-3 rounded-full transition-colors"
            :class="index === currentSlide ? 'bg-blue-400' : 'bg-gray-600 hover:bg-gray-500'"
            :aria-label="`Go to skill group ${index + 1}`" :aria-current="index === currentSlide ? 'true' : 'false'">
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const sectionRef = ref(null)
const currentSlide = ref(0)

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

const skills = [
  { name: 'Vue', icon: 'fab fa-vuejs' },
  { name: 'React', icon: 'fab fa-react' },
  { name: 'Angular', icon: 'fab fa-angular' },
  { name: 'Node.js', icon: 'fab fa-node-js' },
  { name: 'TypeScript', icon: 'fas fa-code' },
  { name: 'Go', icon: 'fas fa-terminal' },
  { name: 'PHP', icon: 'fab fa-php' },
  { name: 'MongoDB', icon: 'fas fa-database' },
  { name: 'PostgreSQL', icon: 'fas fa-database' },
  { name: 'MySQL', icon: 'fas fa-database' },
  { name: 'Express', icon: 'fab fa-node-js' },
  { name: 'Cypress', icon: 'fas fa-vial' }
]

// Group skills into sets of 8 for each slide
const skillGroups = computed(() => {
  const groups = []
  for (let i = 0; i < skills.length; i += 8) {
    groups.push(skills.slice(i, i + 8))
  }
  return groups
})

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % skillGroups.value.length
}

const prevSlide = () => {
  currentSlide.value = currentSlide.value === 0
    ? skillGroups.value.length - 1
    : currentSlide.value - 1
}
</script>
