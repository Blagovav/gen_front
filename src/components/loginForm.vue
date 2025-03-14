<script lang="ts" setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const email = ref('')

const clickHandler = () => {
  router.push({ name: 'home' })
}
</script>

<template>
  <div class="col-6 position-relative">
    <div class="w-100 d-flex justify-content-end">
      <div :class="$style.logo"></div>
    </div>
    <div class="position-absolute w-100 h-100 d-flex justify-content-center align-items-center">
      <div class="form">
        <form :class="$style.form">
          <div class="d-flex flex-column">
            <label>Email</label>
            <input type="email" class="form-control" v-model="email" />
            <button @click="clickHandler" type="button" class="btn btn-primary w-100 mt-2">
              Sign in with Email
            </button>
          </div>
          <div :class="$style.information">
            <p class="m-0">We’ll email you a magic code for a password-free sign in.</p>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style module>
.logo {
  background-image: url('../assets/gen_logo.png');
  background-size: contain;
  background-repeat: no-repeat;
  width: 300px;
  height: 50px;
}

.form {
  width: 480px;
}

.information {
  border: 1px solid rgba(203, 213, 225, 1);

  border-radius: 6px;
  padding: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
  color: rgba(100, 116, 139, 1);

  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
  letter-spacing: 0%;
}
</style>
