<template>
  <div
    class="inline-block w-[240px] h-full shrink-0 mx-2 bg-primary/90 text-white rounded-xl p-4 border border-white/10 transition-transform transform hover:scale-[1.03] hover:border-white hover:cursor-pointer duration-300"
    @click="OpenProject"
    >
    <img
      :src="project.image"
      alt="Project image"
      class="w-full h-32 object-cover rounded-md mb-4 "
    />
    <h3 class="text-lg font-semibold mb-1 leading-tight">{{ project.title }}</h3>
    <p class="text-sm text-white/80 mb-3 break-words whitespace-pre-line">{{ project.description }}</p>
    <div class="flex flex-wrap gap-2">
      <span
        v-for="tag in project.tags"
        :key="tag"
        class="text-xs bg-white/10 text-white px-2 py-1 rounded-full border border-white/20"
      >
        {{ tag }}
      </span>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  project: {
    title: string,
    description: string,
    image: string,
    tags: string[],
    link?: string
  }
}>()

function OpenProject()
{
  const project = props.project;
  if (project.link)
  {
    window.open(project.link, '_blank');
  }
  else
  {
    console.warn('No link provided for project:', project.title);
  }
}
</script>
