<template>
  <div class="container mx-auto py-8 px-4">
    <button @click="router.back()" 
            class="mb-8 flex items-center text-gray-600 hover:text-gray-800 transition-colors">
      <span class="mr-2">←</span> Back to Projects
    </button>
    
    <div v-if="project" class="bg-white rounded-lg shadow-lg overflow-hidden">
      <!-- Hero Section -->
      <div class="relative h-96">
        <img :src="project.image" :alt="project.title" class="w-full h-full object-cover">
        <div class="absolute bottom-0 left-0 right-0 bg-gradient-to-t from-black/70 to-transparent p-8">
          <h1 class="text-4xl font-bold text-white mb-2">{{ project.title }}</h1>
          <div class="flex flex-wrap gap-2">
            <span v-for="tag in project.tags" :key="tag" 
                  class="px-3 py-1 bg-white/20 rounded-full text-sm text-white">
              {{ tag }}
            </span>
          </div>
        </div>
      </div>

      <!-- Project Content -->
      <div class="p-8">
        <!-- Overview -->
        <section class="mb-12">
          <h2 class="text-2xl font-semibold mb-4">Project Overview</h2>
          <p class="text-gray-700 leading-relaxed">{{ project.description }}</p>
        </section>

        <!-- Process -->
        <section class="mb-12">
          <h2 class="text-2xl font-semibold mb-4">Design Process</h2>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div v-for="(phase, index) in project.process" :key="index" 
                 class="p-6 bg-gray-50 rounded-lg">
              <h3 class="text-xl font-semibold mb-3">{{ phase.title }}</h3>
              <p class="text-gray-600">{{ phase.description }}</p>
            </div>
          </div>
        </section>

        <!-- Results -->
        <section class="mb-12">
          <h2 class="text-2xl font-semibold mb-4">Results & Impact</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            <div v-for="(result, index) in project.results" :key="index" 
                 class="flex items-start">
              <div class="mr-4 text-3xl text-blue-500">
                {{ result.stat }}
              </div>
              <div>
                <h4 class="font-semibold mb-1">{{ result.title }}</h4>
                <p class="text-gray-600">{{ result.description }}</p>
              </div>
            </div>
          </div>
        </section>

        <!-- Gallery -->
        <section>
          <h2 class="text-2xl font-semibold mb-4">Project Gallery</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
            <div v-for="(image, index) in project.gallery" :key="index" 
                 class="relative group cursor-pointer"
                 @click="openGallery(index)">
              <img :src="image" :alt="'Project image ' + (index + 1)" 
                   class="w-full h-48 object-cover rounded-lg">
              <div class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 
                          transition-opacity flex items-center justify-center rounded-lg">
                <span class="text-white">Click to enlarge</span>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>

    <!-- Gallery Modal -->
    <div v-if="showGallery" 
         class="fixed inset-0 bg-black/90 z-50 flex items-center justify-center"
         @click="showGallery = false">
      <button @click="prevImage" 
              class="absolute left-4 text-white text-4xl hover:text-gray-300"
              @click.stop>
        ←
      </button>
      <img :src="project.gallery[currentImageIndex]" 
           :alt="'Project image ' + (currentImageIndex + 1)"
           class="max-h-[90vh] max-w-[90vw] object-contain">
      <button @click="nextImage" 
              class="absolute right-4 text-white text-4xl hover:text-gray-300"
              @click.stop>
        →
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import { useRouter, useRoute } from 'vue-router'

const router = useRouter()
const route = useRoute()

// Gallery state
const showGallery = ref(false)
const currentImageIndex = ref(0)

const openGallery = (index: number) => {
  currentImageIndex.value = index
  showGallery.value = true
}

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % project.value.gallery.length
}

const prevImage = () => {
  currentImageIndex.value = currentImageIndex.value === 0 
    ? project.value.gallery.length - 1 
    : currentImageIndex.value - 1
}

// Mock project data (in real app, this would come from an API or store)
const project = computed(() => {
  const projectId = Number(route.params.id)
  return {
    id: projectId,
    title: "E-Commerce Redesign",
    description: "A complete UX/UI overhaul of an e-commerce platform focusing on user experience and conversion optimization. The project involved extensive user research, wireframing, prototyping, and iterative design based on user feedback.",
    image: "/images/project1.jpg",
    tags: ["UX Design", "UI Design", "E-commerce"],
    process: [
      {
        title: "Research",
        description: "Conducted user interviews, surveys, and competitive analysis to understand pain points and opportunities."
      },
      {
        title: "Design",
        description: "Created wireframes, user flows, and high-fidelity prototypes with focus on user-centered design principles."
      },
      {
        title: "Testing",
        description: "Performed usability testing with target users and iterated based on feedback and analytics."
      }
    ],
    results: [
      {
        stat: "+150%",
        title: "Conversion Rate Increase",
        description: "Doubled the conversion rate through improved user experience and checkout flow."
      },
      {
        stat: "-40%",
        title: "Cart Abandonment Reduction",
        description: "Significantly reduced cart abandonment through streamlined checkout process."
      },
      {
        stat: "+85%",
        title: "User Satisfaction",
        description: "Improved user satisfaction scores based on post-launch surveys."
      },
      {
        stat: "4.8/5",
        title: "App Store Rating",
        description: "Maintained high user ratings after the redesign launch."
      }
    ],
    gallery: [
      "/images/project1-detail1.jpg",
      "/images/project1-detail2.jpg",
      "/images/project1-detail3.jpg",
      "/images/project1-detail4.jpg",
      "/images/project1-detail5.jpg",
      "/images/project1-detail6.jpg"
    ]
  }
})
</script>