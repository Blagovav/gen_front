<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Header from '../components/header/index.vue'
import TheCard from '../components/common/TheCard.vue'

const list = ref([
  {},
  {
    id: 1,
    title: 'Zebrafish',
    info: 'Try the process and preview results in this demo project. Its on us, no credits will be used.',
    isDemo: true,
  },
])

onMounted(() => {
  localStorage.removeItem('titleProject')
  localStorage.removeItem('selectedModel')
})
</script>

<template>
  <div class="w-100 h-100">
    <Header></Header>
    <div :class="$style.listWrapper">
      <TheCard v-for="item in list" :key="item?.id" :item="item"></TheCard>
    </div>
  </div>
</template>

<style module>
.listWrapper {
  display: flex;
  gap: 20px;
  padding: 40px;
}
</style>
