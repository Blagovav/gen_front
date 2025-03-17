<script setup lang="ts">
import { computed, onMounted } from 'vue'
import { RouterLink, RouterView, useRouter } from 'vue-router'

const router = useRouter()

onMounted(() => {
  if (!localStorage.getItem('token')) {
    router.push({ name: 'login' })
  }
})
</script>

<template>
  <RouterView />
</template>

<style scoped></style>
