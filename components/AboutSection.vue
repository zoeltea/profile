<template>
  <section ref="sectionRef" id="about" class="py-16 opacity-0 translate-y-10 transition-all duration-700 ease-out">
    <div class="max-w-7xl mx-auto px-4">
      <h2 class="text-3xl md:text-4xl font-bold text-center mb-12 text-white">About Me</h2>
      <p class="text-lg text-gray-300 mb-8 text-center">
        I have been developing since 2012, with over 9 years of experience and more than 50 successful projects.
      </p>
      <div class="flex flex-wrap justify-center gap-8">
        <div
          class="flex flex-col items-center bg-[#121212] p-6 rounded-xl border border-[#252525] hover:border-blue-400 transition-colors w-32">
          <img src="@/assets/icon/bukalapak.png" alt="Bukalapak" class="w-16 h-16 mb-4">
          <span class="text-gray-300 font-medium">Bukalapak</span>
        </div>
        <div
          class="flex flex-col items-center bg-[#121212] p-6 rounded-xl border border-[#252525] hover:border-blue-400 transition-colors w-32">
          <img src="@/assets/icon/edunex.png" alt="Edunex" class="w-16 h-16 mb-4">
          <span class="text-gray-300 font-medium">Edunex</span>
        </div>
        <div
          class="flex flex-col items-center bg-[#121212] p-6 rounded-xl border border-[#252525] hover:border-blue-400 transition-colors w-32">
          <img src="@/assets/icon/bri.png" alt="BRI" class="w-16 h-16 mb-4">
          <span class="text-gray-300 font-medium">BRI</span>
        </div>
        <div
          class="flex flex-col items-center bg-[#121212] p-6 rounded-xl border border-[#252525] hover:border-blue-400 transition-colors w-32">
          <img src="@/assets/icon/maxsol.png" alt="Maxsol" class="w-16 h-16 mb-4">
          <span class="text-gray-300 font-medium">Maxsol</span>
        </div>
      </div>
    </div>
  </section>
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
