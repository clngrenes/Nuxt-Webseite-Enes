<template>
  <div class="border p-4 rounded shadow hover:shadow-lg transition duration-300">
    <h2 class="text-xl font-bold">{{ title }}</h2>
    <p class="mt-2">{{ description }}</p>
  </div>
</template>

<script lang="ts" setup>
defineProps<{
  title: string,
  description: string
}>()
</script>

<style scoped>
</style>