<template>
  <div class="relative w-full overflow-hidden h-[360px] bg-primary p-10 group">
    <div class="flex whitespace-nowrap h-full">
      <div v-for="i in 2" :key="i" class="animate-marquee items-stretch group-hover:[animation-play-state:paused]">
        <ProjectCard
          v-for="project in projects"
          :key="project.id"
          :project="project"
          />
      </div>
    </div>
  </div>
</template>

<script setup>
import projects from '@/data/projects.json';

</script>

<style scoped>
@keyframes marquee {
  0% {
    transform: translateX(0%);
  }
  100% {
    transform: translateX(-100%);
  }
}

.animate-marquee {
  animation: marquee 30s linear infinite;
}
</style>
