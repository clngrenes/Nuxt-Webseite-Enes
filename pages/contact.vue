<template>
  <div class="container mx-auto py-12 px-4">
    <h1 class="text-4xl font-bold mb-8 text-center">Contact Me</h1>
    
    <div class="max-w-3xl mx-auto bg-white shadow-lg rounded-lg overflow-hidden">
      <div class="md:flex">
        <div class="md:w-1/2 p-8 bg-blue-600 text-white">
          <h2 class="text-2xl font-semibold mb-4">Get in Touch</h2>
          <p class="mb-6">
            Have a project in mind or just want to say hello? Feel free to reach out!
          </p>
          
          <div class="space-y-4">
            <div class="flex items-start">
              <span class="mr-3 text-xl">📧</span>
              <div>
                <p class="font-medium">Email</p>
                <p>info@enescilingir.com</p>
              </div>
            </div>
            
            <div class="flex items-start">
              <span class="mr-3 text-xl">📱</span>
              <div>
                <p class="font-medium">Phone</p>
                <p>+49 123 456 7890</p>
              </div>
            </div>
            
            <div class="flex items-start">
              <span class="mr-3 text-xl">📍</span>
              <div>
                <p class="font-medium">Location</p>
                <p>Schwäbisch Gmünd, Germany</p>
              </div>
            </div>
          </div>
        </div>
        
        <div class="md:w-1/2 p-8">
          <h2 class="text-2xl font-semibold mb-4">Send a Message</h2>
          <form @submit.prevent="handleSubmit">
            <div class="mb-4">
              <label for="name" class="block text-gray-700 mb-2">Name</label>
              <input id="name" v-model="formData.name" type="text" 
                     class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:border-blue-500"
                     required>
            </div>
            
            <div class="mb-4">
              <label for="email" class="block text-gray-700 mb-2">Email</label>
              <input id="email" v-model="formData.email" type="email"
                     class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:border-blue-500"
                     required>
            </div>
            
            <div class="mb-4">
              <label for="message" class="block text-gray-700 mb-2">Message</label>
              <textarea id="message" v-model="formData.message"
                        class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:border-blue-500 h-32"
                        required></textarea>
            </div>
            
            <button type="submit" 
                    class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md transition-colors">
              Send Message
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

const formData = reactive({
  name: '',
  email: '',
  message: ''
});

function handleSubmit() {
  // Hier würde die eigentliche Formularverarbeitung stattfinden
  console.log('Form submitted:', formData);
  alert('Thanks for your message! I will get back to you soon.');
  
  // Form zurücksetzen
  formData.name = '';
  formData.email = '';
  formData.message = '';
}
</script>