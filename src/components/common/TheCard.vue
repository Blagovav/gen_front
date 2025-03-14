<script lang="ts" setup>
import { shallowRef } from 'vue'
const props = defineProps({
  item: {
    type: Object,
    required: true,
    default: () => {},
  },
})

const isCreateNewProject = shallowRef(false)
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
      <div class="w-100 h-100" v-else>SALAM</div>
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
