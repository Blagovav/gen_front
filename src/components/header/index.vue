<script lang="ts" setup>
import { useRouter } from 'vue-router'
const router = useRouter()
const logOut = () => {
  localStorage.removeItem('token')
  router.push({ name: 'login' })
}
</script>

<template>
  <div class="d-flex justify-content-between align-items-center w-100 p-2" :class="$style.header">
    <div :class="$style.logo"></div>
    <div class="d-flex">
      <div :class="$style.info">
        <div class="count me-2">
          <span>10 Credits</span>
        </div>
        <div :class="$style.contactUs" class="">
          <span>Contact us to get more</span>
        </div>
      </div>
      <button @click="logOut" type="button" class="ms-3" :class="$style.logOut">Log out</button>
    </div>
  </div>
</template>

<style module>
.header {
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
  letter-spacing: 0%;
}
.logo {
  background-image: url('../../assets/gen_logo.png');
  background-size: contain;
  width: 300px;
  height: 50px;
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

.info {
  display: flex;
  align-items: center;
  border: 1px solid rgba(255, 255, 255, 1);
  border-radius: 6px;
  padding: 5px 5px;
}

.contactUs {
  background-color: rgba(255, 255, 255, 1);
  padding: 5px;
  border-radius: 5px;
}

.logOut {
  display: flex;
  align-items: center;
  border: 1px solid rgba(255, 255, 255, 1);
  border-radius: 6px;
  padding: 5px 15px;
  background-color: transparent;
}
</style>
