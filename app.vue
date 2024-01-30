<script setup lang="ts">
const router = useRouter()

const nav = [
  { label: 'Home', to: '/' },
  { label: 'About', to: '/about' },
  { label: 'Parent (index)', to: '/parent' },
  { label: 'Parent (b)', to: '/parent/b' },
]
</script>

<template>
  <NuxtExample dir="routing/pages" :nav="nav" current-route>
    <NuxtLoadingIndicator />
    <NuxtPage />
  </NuxtExample>
</template>
