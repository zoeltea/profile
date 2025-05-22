<template>
  <Teleport to="body">
    <!-- Root container with high z-index -->
    <div v-if="project" class="fixed inset-0 z-[999]">
      <!-- Backdrop -->
      <Transition name="fade" appear>
        <div v-show="project" class="fixed inset-0 bg-white bg-opacity-50" @click="$emit('close')"></div>
      </Transition>

      <!-- Modal Container -->
      <div class="fixed inset-0 flex items-center justify-center p-4">
        <!-- Modal Content with Animation -->
        <Transition name="modal" appear>
          <div v-show="project" class="relative w-full max-w-3xl" @click.stop>
            <div class="bg-[#1a1a1a] rounded-lg overflow-y-auto max-h-[90vh] border border-[#252525]">
              <div class="p-6">
                <div class="flex justify-between items-start mb-4">
                  <h2 class="text-2xl font-bold text-white">{{ project.title }}</h2>
                  <button @click="$emit('close')" class="text-gray-400 hover:text-gray-200" aria-label="Close modal">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                  </button>
                </div>
                <picture>
                  <source :srcset="project.image.replace('.png', '.webp')" type="image/webp">
                  <img :src="project.image" :alt="project.title" class="w-full rounded-lg mb-4">
                </picture>
                <p class="text-gray-300 mb-4">{{ project.longDescription }}</p>
                <div class="space-y-2">
                  <h3 class="font-semibold text-white">Technologies Used:</h3>
                  <div class="flex flex-wrap gap-2">
                    <span v-for="tech in project.technologies" :key="tech"
                      class="bg-[#121212] text-blue-200 px-3 py-1 rounded-full text-sm border border-[#252525]">
                      {{ tech }}
                    </span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </Transition>
      </div>
    </div>
  </Teleport>
</template>

<style scoped>
/* Backdrop animations */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Modal animations */
.modal-enter-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.modal-leave-active {
  transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: translateY(20px) scale(0.95);
}
</style>

<script setup>
import { Transition, Teleport } from 'vue'
defineProps({
  project: {
    type: Object,
    required: false,
  }
})

defineEmits(['close'])
</script>
