<template>
  <div :class="['min-h-screen', isDark ? 'dark' : '']">
    <Header />
    <main>
      <!-- Hero Section -->
      <section id="hero" class="min-h-screen flex flex-col justify-center items-center px-4 pt-24 pb-16 bg-gradient-to-b from-gray-50 to-gray-100 dark:from-gray-900 dark:to-gray-800">
        <div class="text-center max-w-4xl mx-auto">
          <h1 class="text-5xl md:text-7xl font-bold mb-4 text-gray-900 dark:text-white tracking-tighter animate-fade-in">
            Hey! I am <span class="text-gray-700 dark:text-gray-300">Enes Cilingir</span>
          </h1>
          <p class="text-2xl md:text-3xl mb-6 text-gray-700 dark:text-gray-300 animate-fade-in animation-delay-300">
            An interaction design student
          </p>
          <p class="text-xl md:text-2xl text-gray-600 dark:text-gray-400 mb-12 max-w-3xl mx-auto animate-fade-in animation-delay-500">
            Who enhances the emotional connection between users and brands.
          </p>
          <div class="flex justify-center space-x-6 animate-fade-in animation-delay-700">
            <a href="#projects" class="px-8 py-3 bg-gray-800 dark:bg-gray-700 text-white rounded-full hover:bg-gray-700 dark:hover:bg-gray-600 transition-all hover:scale-105">
              View Projects
            </a>
            <a href="#about" class="px-8 py-3 bg-gray-200 dark:bg-gray-800 text-gray-800 dark:text-gray-200 rounded-full hover:bg-gray-300 dark:hover:bg-gray-700 transition-all hover:scale-105">
              About Me
            </a>
          </div>
        </div>
        <div class="absolute bottom-8 left-0 right-0 flex justify-center animate-bounce">
          <a href="#projects" class="text-gray-500 dark:text-gray-400">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
            </svg>
          </a>
        </div>
      </section>

      <!-- Projects Section -->
      <section id="projects" class="py-20 px-4 bg-white dark:bg-gray-900">
        <div class="container mx-auto">
          <h2 class="text-4xl font-bold mb-12 text-center text-gray-900 dark:text-white">Projects</h2>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
            <!-- Project Items -->
            <div v-for="project in projects" :key="project.id" 
                 class="group relative bg-gray-50 dark:bg-gray-800 rounded-xl overflow-hidden shadow-lg hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2">
              <div class="aspect-w-16 aspect-h-9 overflow-hidden">
                <img :src="project.image" :alt="project.title" class="w-full object-cover transition-transform duration-700 group-hover:scale-105">
              </div>
              <div class="p-6">
                <span class="inline-block px-3 py-1 text-xs font-semibold bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 rounded-full mb-3">
                  {{ project.category }}
                </span>
                <h3 class="text-2xl font-bold mb-2 text-gray-900 dark:text-white">{{ project.title }}</h3>
                <p class="text-gray-600 dark:text-gray-300 mb-4 line-clamp-3">{{ project.description }}</p>
                <div class="flex flex-wrap gap-2 mb-4">
                  <span v-for="tag in project.tags" :key="tag" 
                        class="px-3 py-1 text-xs bg-gray-100 dark:bg-gray-700 text-gray-700 dark:text-gray-300 rounded-full">
                    {{ tag }}
                  </span>
                </div>
                <button @click="openProjectModal(project)" 
                    class="inline-block mt-2 px-5 py-2 bg-gray-800 dark:bg-gray-700 text-white rounded hover:bg-gray-700 dark:hover:bg-gray-600 transition-colors">
                  View Details
                </button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- About Section -->
      <section id="about" class="py-20 px-4 bg-gray-50 dark:bg-gray-800">
        <div class="container mx-auto">
          <h2 class="text-4xl font-bold mb-12 text-center text-gray-900 dark:text-white">About Me</h2>
          <div class="flex flex-col md:flex-row items-center gap-12 max-w-5xl mx-auto">
            <div class="md:w-2/5">
              <div class="rounded-3xl overflow-hidden shadow-xl transform transition-all hover:scale-105 duration-500 relative">
                <img src="/images/enescilingir.jpg" alt="Enes Cilingir" class="w-full">
                <div class="absolute inset-0 bg-gradient-to-t from-gray-900 to-transparent opacity-50"></div>
              </div>
            </div>
            <div class="md:w-3/5">
              <p class="text-lg text-gray-700 dark:text-gray-300 mb-6 leading-relaxed">
                I am Enes Cilingir, an Interaction Design student at the University of Applied Sciences in Schwäbisch Gmund. My design journey began in 2017, evolving from brand identity work for tech startups to my current focus on user-centered digital experiences.
              </p>
              <p class="text-lg text-gray-700 dark:text-gray-300 mb-8 leading-relaxed">
                Over the years, I've built my own online presence while working with diverse clients as a freelancer. My goal is to create inspiring brands and meaningful experiences through design that truly resonates with users. I'm eager to join innovative teams where I can apply my UX/UI design passion to impactful projects.
              </p>
              <div class="mb-8">
                <h3 class="text-xl font-semibold mb-4 text-gray-900 dark:text-white">Interests</h3>
                <div class="flex flex-wrap gap-3">
                  <div class="px-4 py-2 bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 rounded-full">Art</div>
                  <div class="px-4 py-2 bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 rounded-full">Fitness Training</div>
                  <div class="px-4 py-2 bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 rounded-full">Quality Time with Friends & Family</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Contact Section -->
      <section id="contact" class="py-20 px-4 bg-white dark:bg-gray-900">
        <div class="container mx-auto max-w-5xl">
          <h2 class="text-4xl font-bold mb-12 text-center text-gray-900 dark:text-white">Get In Touch</h2>
          <div class="flex flex-col md:flex-row gap-12">
            <div class="md:w-1/2">
              <h3 class="text-2xl font-bold mb-6 text-gray-900 dark:text-white">Contact Information</h3>
              <div class="space-y-6">
                <div class="flex items-start">
                  <div class="mr-4 p-3 bg-gray-100 dark:bg-gray-800 rounded-full">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-700 dark:text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                    </svg>
                  </div>
                  <div>
                    <h4 class="text-lg font-semibold text-gray-900 dark:text-white">Email</h4>
                    <a href="mailto:info@enescilingir.com" class="text-gray-600 dark:text-gray-300 hover:text-gray-800 dark:hover:text-white">info@enescilingir.com</a>
                  </div>
                </div>
                <div class="flex items-start">
                  <div class="mr-4 p-3 bg-gray-100 dark:bg-gray-800 rounded-full">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-700 dark:text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                    </svg>
                  </div>
                  <div>
                    <h4 class="text-lg font-semibold text-gray-900 dark:text-white">Phone</h4>
                    <p class="text-gray-600 dark:text-gray-300">+49 123 456 7890</p>
                  </div>
                </div>
                <div class="flex items-start">
                  <div class="mr-4 p-3 bg-gray-100 dark:bg-gray-800 rounded-full">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-700 dark:text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                    </svg>
                  </div>
                  <div>
                    <h4 class="text-lg font-semibold text-gray-900 dark:text-white">Location</h4>
                    <p class="text-gray-600 dark:text-gray-300">Schwäbisch Gmünd, Germany</p>
                  </div>
                </div>
              </div>
            </div>
            <div class="md:w-1/2">
              <h3 class="text-2xl font-bold mb-6 text-gray-900 dark:text-white">Send a Message</h3>
              <form @submit.prevent="handleContactSubmit" class="space-y-4">
                <div>
                  <label for="name" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Name</label>
                  <input v-model="contactForm.name" type="text" id="name" required class="w-full px-4 py-3 rounded-lg bg-gray-100 dark:bg-gray-800 border border-gray-300 dark:border-gray-700 text-gray-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-gray-500">
                </div>
                <div>
                  <label for="email" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Email</label>
                  <input v-model="contactForm.email" type="email" id="email" required class="w-full px-4 py-3 rounded-lg bg-gray-100 dark:bg-gray-800 border border-gray-300 dark:border-gray-700 text-gray-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-gray-500">
                </div>
                <div>
                  <label for="message" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">Message</label>
                  <textarea v-model="contactForm.message" id="message" rows="5" required class="w-full px-4 py-3 rounded-lg bg-gray-100 dark:bg-gray-800 border border-gray-300 dark:border-gray-700 text-gray-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-gray-500"></textarea>
                </div>
                <button type="submit" class="w-full px-8 py-3 bg-gray-800 dark:bg-gray-700 text-white rounded-lg hover:bg-gray-700 dark:hover:bg-gray-600 transition-all hover:scale-105 focus:outline-none">
                  Send Message
                </button>
              </form>
            </div>
          </div>
        </div>
      </section>
    </main>

    <Footer />

    <!-- Project Detail Modal -->
    <Transition name="fade">
      <div v-if="selectedProject" class="fixed inset-0 z-50 flex items-center justify-center">
        <div class="absolute inset-0 bg-black/80 backdrop-blur-sm" @click="selectedProject = null"></div>
        <div class="relative bg-white dark:bg-gray-800 rounded-xl overflow-auto max-h-[90vh] max-w-5xl w-full mx-4 p-6 lg:p-8 shadow-2xl">
          <button @click="selectedProject = null" class="absolute top-4 right-4 p-2 rounded-full bg-gray-100 dark:bg-gray-700 hover:bg-gray-200 dark:hover:bg-gray-600 transition-colors">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-600 dark:text-gray-300" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>

          <h3 class="text-3xl font-bold mb-1 text-gray-900 dark:text-white">{{ selectedProject?.title }}</h3>
          <span class="inline-block px-3 py-1 text-xs font-semibold bg-gray-200 dark:bg-gray-700 text-gray-800 dark:text-gray-200 rounded-full mb-4">
            {{ selectedProject?.category }}
          </span>
          
          <img :src="selectedProject?.image" :alt="selectedProject?.title" class="w-full h-80 object-cover rounded-lg mb-6">
          
          <p class="text-lg text-gray-700 dark:text-gray-300 mb-6 leading-relaxed">{{ selectedProject?.description }}</p>
          
          <div class="mb-6">
            <h4 class="text-xl font-semibold mb-3 text-gray-900 dark:text-white">Technologies</h4>
            <div class="flex flex-wrap gap-2">
              <span v-for="tag in selectedProject?.tags" :key="tag" 
                  class="px-3 py-1 text-sm bg-gray-100 dark:bg-gray-700 text-gray-700 dark:text-gray-300 rounded-full">
                {{ tag }}
              </span>
            </div>
          </div>
          
          <div class="text-center mt-8">
            <button @click="selectedProject = null" class="inline-block px-6 py-2 border border-gray-300 dark:border-gray-600 text-gray-700 dark:text-gray-300 rounded hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors">
              Close
            </button>
          </div>
        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive, onMounted } from 'vue'

// Define Project type
interface Project {
  id: number;
  title: string;
  category: string;
  description: string;
  image: string;
  tags: string[];
}

// Theme state from Header component
const isDark = ref(true)

// Project data
const projects: Project[] = [
  {
    id: 1,
    title: "Pulse",
    category: "INTERACTION DESIGN",
    description: "A quick look into real-time health tracking for everyday users. This concept explores seamless integration of wearable tech.",
    image: "/images/pulse.jpg",
    tags: ["UX Design", "UI Design", "Health Tech"]
  },
  {
    id: 2,
    title: "Hybrid Wallet",
    category: "INTERACTION DESIGN",
    description: "An innovative solution that bridges the gap between traditional cash and modern digital payment.",
    image: "/images/hybrid.jpg",
    tags: ["Mobile App", "FinTech", "UI Design"]
  },
  {
    id: 3,
    title: "Reach",
    category: "UX/UI CASE STUDY",
    description: "The new way to stay connected with your loved ones. Select only the phone contacts you plan to engage with.",
    image: "/images/reach.jpg",
    tags: ["Mobile App", "Social", "UX Research"]
  },
  {
    id: 4,
    title: "ReTarget Media Inc.",
    category: "BRAND IDENTITY DESIGN",
    description: "A social media marketing agency focusing on defining the target customer group of businesses.",
    image: "/images/retarget.jpg",
    tags: ["Branding", "Marketing", "Design System"]
  }
]

// Modal state
const selectedProject = ref<Project | null>(null)

// Contact form
const contactForm = reactive({
  name: '',
  email: '',
  message: ''
})

// Functions
function openProjectModal(project: Project): void {
  selectedProject.value = project
  document.body.classList.add('overflow-hidden')
}

function handleContactSubmit(): void {
  // Here would be your form submission logic
  alert('Thank you for your message! I will get back to you soon.')
  contactForm.name = ''
  contactForm.email = ''
  contactForm.message = ''
}

// Initialize Geist font
onMounted(() => {
  // Dynamically load Geist font
  const link = document.createElement('link')
  link.rel = 'stylesheet'
  link.href = 'https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap' // Using Plus Jakarta Sans as closest to Geist
  document.head.appendChild(link)
  
  // Add smooth scroll behavior
  document.documentElement.style.scrollBehavior = 'smooth'
})
</script>

<style>
/* Main styles */
:root {
  font-family: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, sans-serif;
}

/* Animation classes */
.animate-fade-in {
  animation: fadeIn 1s ease forwards;
  opacity: 0;
}

.animation-delay-300 {
  animation-delay: 300ms;
}

.animation-delay-500 {
  animation-delay: 500ms;
}

.animation-delay-700 {
  animation-delay: 700ms;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Modal transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.aspect-w-16 {
  aspect-ratio: 16 / 9;
}

/* Line clamp for project descriptions */
.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  line-clamp: 3; /* Standard property added for compatibility */
}
</style>



