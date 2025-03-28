<template>
  <div
    class="image-uploader"
    :class="{ 'drag-over': updateImages.length }"
    @dragover.prevent="handleDragOver"
    @dragenter.prevent="handleDragEnter"
    @dragleave.prevent="handleDragLeave"
    @drop.prevent="handleDrop"
  >
    <!-- Зона для перетаскивания -->
    <div v-if="!updateImages.length" class="drop-zone" @click="openFilePicker">
      <img src="@/assets/dragDropIcon.svg" />
      <p class="m-0 mt-3">Drag 'n' drop an image here,</p>
      <p class="m-0 mb-5">or click to select a file</p>
      <span>Supports: PNG, JPG, TIF</span>
    </div>

    <!-- Отображение загруженных изображений -->
    <div v-else class="uploaded-images">
      <div v-for="(image, index) in updateImages" :key="index" class="image-preview">
        <img :src="image" alt="Uploaded Image" />
      </div>
      <div class="add-image" @click="openFilePicker">
        <p>+</p>
        <p>Add images</p>
        <p style="font-size: 12px; color: #666">You can add more images to the project later</p>
      </div>
    </div>

    <!-- Кнопка выбора файла -->
    <input
      ref="fileInput"
      type="file"
      accept=".png,.jpg,.tif"
      @change="handleFileSelect"
      style="display: none"
    />
  </div>
</template>

<script lang="ts" setup>
import { ref, computed } from 'vue'

const props = defineProps({
  images: {
    type: Array,
    default: () => [],
  },
})

const emit = defineEmits(['update:images'])

const updateImages = computed({
  get() {
    return props.images
  },
  set(value) {
    emit('update:images', value)
  },
})

const isDragging = ref(false) // Флаг для отслеживания состояния перетаскивания

// Функция для обработки перетаскивания
const handleDragOver = (event: DragEvent): void => {
  event.preventDefault()
}

const handleDragEnter = (): void => {
  isDragging.value = true
}

const handleDragLeave = (): void => {
  isDragging.value = false
}

// Функция для обработки события "drop"
const handleDrop = (event: DragEvent): void => {
  event.preventDefault()
  isDragging.value = false

  const files = event.dataTransfer?.files
  if (files && files.length > 0) {
    handleFiles(files)
  }
}

// Функция для обработки выбора файла через кнопку
const handleFileSelect = (event: Event): void => {
  const inputElement = event.target as HTMLInputElement
  const files = inputElement.files
  if (files && files.length > 0) {
    handleFiles(files)
  }
}

// Функция для обработки массива файлов
const handleFiles = (files: FileList): void => {
  for (let i = 0; i < files.length; i++) {
    const file = files[i]
    if (['image/png', 'image/jpeg', 'image/tiff'].includes(file.type)) {
      const reader = new FileReader()
      reader.onload = (e) => {
        if (e.target?.result) {
          updateImages.value.push(e.target.result as string)
        }
      }
      reader.readAsDataURL(file)
    } else {
      alert('Unsupported file type. Please upload PNG, JPG, or TIF files.')
    }
  }
}

// Функция для открытия диалогового окна выбора файла
const openFilePicker = (): void => {
  const fileInput = document.querySelector('input[type="file"]')
  if (fileInput) {
    fileInput.click()
  }
}
</script>

<style scoped>
.image-uploader {
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px dashed rgba(130, 130, 130, 1);
  border-radius: 8px;
  padding: 20px;
  min-height: 596px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.drop-zone {
  text-align: center;
  font-size: 14px;
  color: #666;
}

.drop-zone p {
  font-weight: 400;
  font-size: 16px;
  line-height: 146%;
  letter-spacing: 0%;
  text-align: center;
  color: rgba(0, 0, 0, 1);
}

.drop-zone span {
  font-family: Inter;
  font-weight: 400;
  font-size: 16px;
  line-height: 146%;
  letter-spacing: 0%;
  text-align: center;
  color: rgba(138, 138, 138, 1);
}

.uploaded-images {
  display: flex;
  gap: 10px;
}

.image-preview {
  width: 266px;
  height: 335px;

  border-radius: 8px;
  overflow: hidden;
  position: relative;
}

.image-preview img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.drag-over {
  justify-content: left;
  align-items: self-start;
  background-color: transparent;
  border: none;
}

.add-image {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 266px;
  height: 335px;
  border: 1px solid #ccc;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-image:hover {
  background-color: #f0f0f0;
}

.add-image svg {
  width: 30px;
  height: 30px;
  margin-bottom: 5px;
}
</style>
