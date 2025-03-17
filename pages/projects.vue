<template>
  <div class="container mx-auto py-8 px-4">
    <h1 class="text-4xl font-bold mb-8">Projects</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <!-- Project Cards -->
      <div v-for="project in projects" :key="project.id" 
           class="bg-white rounded-lg shadow-lg overflow-hidden transform transition-all duration-300 hover:scale-105">
        <img :src="project.image" :alt="project.title" class="w-full h-64 object-cover">
        <div class="p-6">
          <div class="mb-4">
            <span class="bg-gray-100 text-gray-700 px-3 py-1 rounded-full text-sm font-medium">
              {{ project.category }}
            </span>
          </div>
          <h3 class="text-2xl font-semibold mb-2">{{ project.title }}</h3>
          <p class="text-gray-600 mb-4">{{ project.description }}</p>
          <div class="flex flex-wrap gap-2 mb-4">
            <span v-for="tag in project.tags" :key="tag" 
                  class="px-3 py-1 bg-gray-100 rounded-full text-sm text-gray-700">
              {{ tag }}
            </span>
          </div>
          <NuxtLink :to="'/project/' + project.id" 
                    class="inline-block bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition-colors">
            View Details
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const projects = [
  {
    id: 1,
    title: "Pulse",
    category: "INTERACTION DESIGN",
    description: "A quick look into real-time health tracking for everyday users. This concept explores seamless integration of wearable tech.",
    image: "/images/pulse.jpg", // Korrigiert: Entferne "public" aus dem Pfad
    tags: ["UX Design", "UI Design", "Health Tech"]
  },
  {
    id: 2,
    title: "Hybrid Wallet",
    category: "INTERACTION DESIGN",
    description: "An innovative solution that bridges the gap between traditional cash and modern digital payment.",
    image: "/images/hybrid.jpg", // Korrigiert: Entferne "public" aus dem Pfad
    tags: ["Mobile App", "FinTech", "UI Design"]
  },
  {
    id: 3,
    title: "Reach",
    category: "UX/UI CASE STUDY",
    description: "The new way to stay connected with your loved ones. Select only the phone contacts you plan to engage with.",
    image: "/images/reach.jpg", // Korrigiert: Entferne "public" aus dem Pfad
    tags: ["Mobile App", "Social", "UX Research"]
  },
  {
    id: 4,
    title: "ReTarget Media Inc.",
    category: "BRAND IDENTITY DESIGN",
    description: "A social media marketing agency focusing on defining the target customer group of businesses.",
    image: "/images/retarget.jpg", // Korrigiert: Entferne "public" aus dem Pfad
    tags: ["Branding", "Marketing", "Design System"]
  }
]
</script>

<style scoped>
/* Hier können weitere Styles ergänzt werden */
</style>