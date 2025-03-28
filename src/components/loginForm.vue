<script lang="ts" setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const email = ref('')
const isShowInputCode = ref(false)
const isShowError = ref(false)

const clickHandler = () => {
  console.log(isValidEmail(email.value))
  if (isValidEmail(email.value)) {
    isShowInputCode.value = true
  } else {
    isShowError.value = true
  }
  // router.push({ name: 'home' })
  // localStorage.setItem('token', email.value)
}

function isValidEmail(email: string) {
  // Регулярное выражение для проверки email
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/

  // Проверяем, соответствует ли email регулярному выражению
  return emailRegex.test(email)
}

const digits = ref<(string | null)[]>([null, null, null, null])

// Функция для обработки вставки текста
const handlePaste = (event: ClipboardEvent): void => {
  event.preventDefault() // Отменяем стандартное поведение вставки

  // Получаем вставленный текст из буфера обмена
  const pastedText = event.clipboardData?.getData('text') || ''

  // Разбиваем текст на отдельные символы (цифры)
  const pastedDigits = pastedText.split('').filter((char) => /\d/.test(char))

  // Распределяем цифры по массиву `digits`
  pastedDigits.forEach((digit, index) => {
    if (index < digits.value.length) {
      digits.value[index] = digit // Обновляем значение в массиве
    }
  })
}

const submit = () => {
  if (digits.value.join('') === '1234') {
    router.push({ name: 'home' })
  }
}
</script>

<template>
  <div class="col-6 position-relative">
    <div class="w-100 d-flex justify-content-end">
      <div :class="$style.logo"></div>
    </div>
    <div class="ms-4" :class="$style.back" v-if="isShowInputCode">
      <a @click.prevent="isShowInputCode = false"><- Back</a>
    </div>
    <div class="position-absolute w-100 h-100 d-flex justify-content-center align-items-center">
      <div class="form">
        <form :class="$style.form" @keydown.enter.prevent="submit">
          <div v-if="isShowInputCode" class="d-flex flex-column align-items-center">
            <label class="mb-2">Your one time password</label>
            <div class="d-flex" :class="$style.code">
              <input
                v-for="(digit, index) in digits"
                :key="index"
                type="text"
                maxlength="1"
                v-model="digits[index]"
                @paste="handlePaste"
              />
            </div>
            <div :class="$style.information">
              <p class="m-0">
                Copy the password from the email or click the magic link. If you haven't received
                the email, just to <a>resend it</a>.
              </p>
            </div>
          </div>
          <div v-else class="d-flex flex-column">
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

.code input {
  border: 1px solid rgba(203, 213, 225, 1);
  width: 65px;
  height: 49px;
  background-color: transparent;
  text-align: center;
  color: black;
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

input[type='number']::-webkit-inner-spin-button,
input[type='number']::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0; /* Убираем отступы */
}

/* Для Firefox */
input[type='number'] {
  -moz-appearance: textfield; /* Отключаем спиннеры */
}
</style>
