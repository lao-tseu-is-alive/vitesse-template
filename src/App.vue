<script setup lang="ts">
import project from '../package.json'

const projectVersion = project.version
const projectName = project.name
const projectDescription = project.description

// https://github.com/vueuse/head
// you can use this to manipulate the document head in any components,
// they will be rendered correctly in the html results with vite-ssg
useHead({
  title: `${projectName}: v${projectVersion}`,
  meta: [
    {
      name: 'description',
      content: `${projectDescription}`,
    },
    {
      name: 'theme-color',
      content: () => isDark.value ? '#00aba9' : '#ffffff',
    },
  ],
  link: [
    {
      rel: 'icon',
      type: 'image/svg+xml',
      href: () => preferredDark.value ? '/favicon-dark.svg' : '/favicon.svg',
    },
  ],
})
</script>

<template>
  <RouterView />
</template>
