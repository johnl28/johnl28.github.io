<script setup lang="ts">
import socialLinks from '@/data/social-links.json'
import profile from '@/data/profile.json';

import profileImage from '@/assets/images/john.jpg'

useHead({
  title: 'Home',
  meta: [
    { name: 'description', content: 'This is the home page of our Nuxt application.' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ]
})

</script>

<template>
  <div class="min-h-screen bg-white dark:bg-black text-gray-900 dark:text-gray-100 flex flex-col items-center justify-center relative transition-colors">
    <!-- Social Links (Top Left) -->
   <div class="absolute top-4 right-4 flex space-x-3">
      <a
        v-for="(link, index) in socialLinks"
        :key="index"
        :href="link.url"
        :aria-label="link.label"
        class="inline-flex items-center justify-center w-10 h-10 rounded-full border border-black dark:border-white bg-white dark:bg-black shadow-sm hover:shadow-md hover:scale-105 transition-all duration-200 text-black dark:text-white hover:bg-black hover:text-white dark:hover:bg-white dark:hover:text-black"
        target="_blank"
      >
        <i :class="link.icon + ' text-lg'"></i>
      </a>
      <a
        href="#projects"
        class="px-4 py-2 rounded-full border border-black dark:border-white bg-white dark:bg-black text-black dark:text-white font-medium shadow hover:bg-black hover:text-white dark:hover:bg-white dark:hover:text-black transition duration-200"
      >
        Projects
      </a>
    </div>

    <!-- Centered Content -->
    <div
      class="text-center px-4 opacity-0 translate-y-8 animate-fade-slide-in"
    >
      <img :src="profileImage" :alt="profile.name" class="w-40 h-40 rounded-full mx-auto mb-6 shadow-xl object-cover border-4 border-gray-200 dark:border-gray-700" />
      <h1 class="text-4xl font-bold mb-3">{{ profile.name }}</h1>
      <p class="text-lg max-w-2xl mx-auto leading-relaxed text-gray-700 dark:text-gray-300">
        {{ profile.description }}
      </p>
    </div>
  </div>
</template>


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
