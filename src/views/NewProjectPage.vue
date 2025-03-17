<script setup lang="ts">
import { ref, computed } from 'vue'
import Header from '../components/header/index.vue'
import FileUpload from 'primevue/fileupload'

const title = computed(() => {
  return localStorage.getItem('titleProject')
})

const selectedModel = computed(() => {
  return localStorage.getItem('selectedModel')
})

const onAdvancedUpload = () => {}
</script>

<template>
  <div class="w-100 h-100">
    <Header></Header>
    <div class="w-100 p-5">
      <router-link to="/"><- To all projects</router-link>
      <div class="title mt-3" :class="$style.selectedModel">{{ selectedModel }}</div>
      <div class="title mb-3 mt-1" :class="$style.title">{{ title }}</div>
      <div class="file-upload">
        <FileUpload
          name="demo[]"
          url="/api/upload"
          @upload="onAdvancedUpload($event)"
          :multiple="true"
          accept="image/*"
          :maxFileSize="1000000"
        >
          <template #empty>
            <span>Drag and drop files to here to upload.</span>
          </template>
        </FileUpload>
      </div>
    </div>
  </div>
</template>

<style module>
.title {
  font-family: Georgia;
  font-weight: 700;
  font-size: 31.76px;
  line-height: 100%;
  letter-spacing: 0%;
  color: rgba(0, 0, 0, 1);
}

.selectedModel {
  font-family: Georgia;
  font-weight: 400;
  font-size: 13px;
  line-height: 100%;
  letter-spacing: 0%;
}
</style>
