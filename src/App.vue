<script setup lang="ts">
  import { onMounted } from 'vue'

  const tele = (window as any).Telegram.WebApp

  onMounted(() => {
    tele.ready()
  })
</script>

<template>
  <router-view />
</template>

<style scoped></style>
