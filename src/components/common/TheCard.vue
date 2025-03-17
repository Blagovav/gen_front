<script lang="ts" setup>
import { shallowRef, ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const props = defineProps({
  item: {
    type: Object,
    required: true,
    default: () => {},
  },
})

const isCreateNewProject = shallowRef(false)
const selectOption = ref('')

const options = ref(['model 1', 'model 2', 'model 3'])

const createProject = () => {
  if (!selectOption.value) return
  localStorage.setItem('titleProject', selectOption.value)
  router.push('/new_project')
}
</script>

<template>
  <div :class="$style.card">
    <div v-if="item.title">
      <div :class="$style.demo" v-if="item.isDemo">Demo</div>
      <div :class="$style.title">{{ item.title }}</div>
      <div :class="$style.info">{{ item.info }}</div>
      <div :class="$style.image"></div>
    </div>
    <div v-else class="d-flex w-100 h-100 justify-content-center align-items-center">
      <button
        @click="isCreateNewProject = !isCreateNewProject"
        class="btn w-100 h-100"
        v-if="!isCreateNewProject"
      >
        <span>+</span><br />New project
      </button>
      <div class="w-100 h-100 d-flex flex-column justify-content-between" v-else>
        <div class="w-100 h-100">
          <div class="title mb-2">
            <p class="m-0">New project</p>
            <span>Create project for better</span>
          </div>
          <div class="d-flex flex-column mb-3">
            <label class="mb-2">Project name</label>
            <input class="form-control" placeholder="e.g. Lab #1" />
          </div>
          <div class="d-flex flex-column">
            <select placeholder="select model" class="form-control" v-model="selectOption">
              <option value="" disabled selected>Select your option</option>
              <option :value="option" v-for="option in options">{{ option }}</option>
            </select>
          </div>
        </div>
        <div>
          <button @click="createProject" type="button" class="btn w-100 mt-2 btn-primary">
            Create project
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style module>
.card {
  width: 266px;
  height: 410px;
  border-radius: 20px;
  border-width: 1px;
  border: 1px solid rgba(244, 245, 247, 1);
  background-color: transparent;
  padding: 20px;
  position: relative;
  overflow: hidden;
}

.title {
  font-family: Georgia;
  font-weight: 700;
  font-size: 31.76px;
  line-height: 100%;
  letter-spacing: 0%;
  margin-top: 40px;
  margin-bottom: 10px;
}

.info {
  font-weight: 400;
  font-size: 13.23px;
  line-height: 150%;
  letter-spacing: 0%;
  padding-right: 20px;
}

.demo {
  position: absolute;
  top: 15px;
  right: 15px;
  padding: 5px 10px;
  border-radius: 6px;
  font-size: 12px;
  background-color: rgba(55, 115, 218, 1);
  color: rgba(255, 255, 255, 1);
}

.image {
  position: absolute;
  bottom: 0px;
  right: 0px;
  width: 81%;
  height: 224px;

  background-image: url('../../assets/card_image.png');
  background-size: contain;
  background-position: bottom;
  background-repeat: no-repeat;
}
</style>
