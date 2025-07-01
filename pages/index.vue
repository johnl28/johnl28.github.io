<template>
  <div :class="['min-h-screen transition-colors flex flex-col items-center justify-center relative', 'bg-[#1a1a1a] text-white']">
    <!-- Social Links (Top Left) -->
    <div class="absolute top-4 right-4 flex space-x-3 p-5">
      <a
        v-for="(link, index) in socialLinks"
        :key="index"
        :href="link.url"
        :aria-label="link.label"
        class="inline-flex items-center justify-center w-10 h-10 rounded-full border border-transparent bg-gradient-to-br from-white to-gray-100 dark:from-[#2a2a2a] dark:to-[#1a1a1a] shadow-md hover:from-gray-200 hover:to-white dark:hover:from-[#3a3a3a] dark:hover:to-[#2a2a2a] transition-all duration-200 text-black dark:text-white"
        target="_blank"
      >
        <i :class="link.icon + ' text-lg'"></i>
      </a>
      <a
        :href="profile.resume_link"
        class="px-4 py-2 rounded-full bg-gradient-to-br from-black to-gray-800 text-white dark:from-white dark:to-gray-200 dark:text-black font-semibold shadow hover:from-gray-900 hover:to-black dark:hover:from-gray-100 dark:hover:to-white transition duration-200"
      >
        Résumé
      </a>
     
    </div>

    <!-- Centered Content -->
    <div class="text-center px-4 opacity-0 translate-y-8 animate-fade-slide-in">
      <img :src="profileImage" :alt="profile.name" class="w-40 h-40 rounded-full mx-auto mb-6 shadow-xl object-cover border-4 border-black dark:border-white" />
      <h1 class="text-4xl font-bold mb-3">{{ profile.name }}</h1>
      <p class="text-lg max-w-2xl mx-auto leading-relaxed text-black dark:text-white">
        {{ profile.description }}
      </p>
    </div>
    
    <!-- Projects Slider -->
    <div class="container">
      <ProjectsSlider></ProjectsSlider>
    </div>
  </div>
</template>

<script setup lang="ts">
import socialLinks from '@/data/social-links.json'
import profile from '@/data/profile.json';

import profileImage from '@/assets/images/john.jpg'

useHead({
  title: 'John Criste - Home',
  meta: [
    { name: 'description', content: 'Welcome to my page!' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ]
})

</script>


<style>
/* Include font-awesome for icons */
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css');

@keyframes fade-slide-in {
  0% {
    opacity: 0;
    transform: translateY(32px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-slide-in {
  animation: fade-slide-in 0.8s ease-out forwards;
}
</style>
