<script setup lang="ts">
import { ref, computed } from 'vue'
import Header from '../components/header/index.vue'
import FileUpload from 'primevue/fileupload'
import fileLoader from '@/components/common/fileLoader.vue'

const title = computed(() => {
  return localStorage.getItem('titleProject')
})

const selectedModel = computed(() => {
  return localStorage.getItem('selectedModel')
})

const images = ref<string[]>([]) // Массив для хранения URL-адресов загруженных изображений
</script>

<template>
  <div class="w-100 h-100">
    <Header></Header>
    <div class="w-100 p-5">
      <router-link to="/"><- To all projects</router-link>
      <div class="title mt-3" :class="$style.selectedModel">{{ selectedModel }}</div>
      <div class="title mb-3 mt-1" :class="$style.title">{{ title }}</div>
      <div class="file-upload">
        <fileLoader v-model:images="images"></fileLoader>
      </div>
      <div class="row d-flex align-items-center mt-2">
        <div class="col-9">
          <div :class="$style.info">
            <img class="me-2" src="@/assets/information.svg" />
            <p class="m-0">
              For better results images should be a) b) c). Hover to see example 1, example 2,
              example 3
            </p>
          </div>
        </div>
        <div class="col-3">
          <div class="d-flex flex-column">
            <button :class="[$style.button, { [$style.active]: images.length > 0 }]" type="button">
              Annotate: {{ images.length }} image for {{ images.length }} credit
            </button>
            <div>
              <p class="m-0 mt-2" :class="$style.textAnnotation">
                Once the annotation is launched, the process cannot be stopped.
              </p>
            </div>
          </div>
        </div>
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

.info {
  border: 1px solid rgba(203, 213, 225, 1);
  border-radius: 6px;
  padding: 20px;
  display: flex;
  color: rgba(100, 116, 139, 1);
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
  letter-spacing: 0%;
}

.info p {
  width: 35%;
}

.button {
  width: 281;
  height: 40;
  top: 871px;
  left: 1106px;
  border-radius: 6px;
  gap: 10px;
  padding-top: 8px;
  padding-right: 16px;
  padding-bottom: 8px;
  padding-left: 16px;
  background-color: rgba(230, 237, 243, 1);
  color: rgba(15, 23, 42, 1);
  outline: none;
  border: none;
}

.button.active {
  color: rgba(255, 255, 255, 1);
  background-color: rgba(29, 115, 225, 1);
}

.textAnnotation {
  font-family: Inter;
  font-weight: 500;
  font-size: 14px;
  line-height: 14px;
  letter-spacing: 0%;
  text-align: center;
  color: rgba(100, 116, 139, 1);
}
</style>
