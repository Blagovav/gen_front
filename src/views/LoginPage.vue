<script lang="ts" setup>
import { ref } from 'vue'
import loginInfo from '../components/loginInfo.vue'
import loginForm from '../components/loginForm.vue'
</script>

<template>
  <div class="w-100 h-100">
    <div class="row" :class="$style.loginPage">
      <loginInfo />
      <loginForm />
    </div>
  </div>
</template>

<style module>
.loginPage {
  height: 100%;
}
</style>
