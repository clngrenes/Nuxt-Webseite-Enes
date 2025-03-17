<template>
  <header :class="[
    'fixed top-0 left-0 right-0 z-50 p-4 flex justify-between items-center transition-colors duration-300',
    isDark ? 'bg-gray-900 shadow-gray-800/30' : 'bg-white shadow-md'
  ]">
    <div class="flex items-center">
      <NuxtLink to="/" :class="[
        'text-xl font-bold',
        isDark ? 'text-white' : 'text-gray-900'
      ]">Enes Cilingir</NuxtLink>
    </div>
    <div class="flex items-center gap-6">
      <nav class="flex gap-6">
        <NuxtLink 
          v-for="(item, index) in navItems" 
          :key="index" 
          :to="item.path"
          :class="[
            'transition-colors',
            isDark ? 'text-gray-300 hover:text-white' : 'text-gray-700 hover:text-black'
          ]"
          :active-class="isDark ? 'text-white font-medium' : 'text-black font-medium'"
        >
          {{ item.title }}
        </NuxtLink>
      </nav>
      
      <!-- Theme toggle button -->
      <button 
        @click="toggleDarkMode" 
        :class="[
          'p-2 rounded-full',
          isDark ? 'bg-gray-800 text-gray-200' : 'bg-gray-100 text-gray-700'
        ]"
        aria-label="Toggle dark mode"
      >
        <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
        </svg>
        <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
        </svg>
      </button>
    </div>
  </header>
  <!-- Spacer to prevent content from going under fixed header -->
  <div class="h-16"></div>
</template>

<script setup lang="ts">
// Theme state
const isDark = ref(true); // Startet im Dark Mode

// Navigation items
const navItems = [
  { title: 'Home', path: '/' },
  { title: 'Projects', path: '/projects' },
  { title: 'About', path: '/about' },
  { title: 'Contact', path: '/contact' }
];

// Toggle dark mode function
function toggleDarkMode() {
  isDark.value = !isDark.value;
  
  // Update document class for global styling
  if (isDark.value) {
    document.documentElement.classList.add('dark');
  } else {
    document.documentElement.classList.remove('dark');
  }
  
  // Save preference to localStorage
  localStorage.setItem('darkMode', isDark.value ? 'true' : 'false');
}

// Initialize dark mode from saved preference or system preference
onMounted(() => {
  const savedDarkMode = localStorage.getItem('darkMode');
  
  if (savedDarkMode !== null) {
    isDark.value = savedDarkMode === 'true';
  }
  
  // Update document class
  if (isDark.value) {
    document.documentElement.classList.add('dark');
  } else {
    document.documentElement.classList.remove('dark');
  }
});
</script>

<style scoped>
a.router-link-active {
  font-weight: bold;
}

/* Dark mode active link styles handled by dynamic classes */
</style>
