<script setup>
import { ref, onMounted } from 'vue'

const email = ref('')
const password = ref('')
const phone = ref('')
const activeForm = ref(0)

function next() {
  if (activeForm.value >= 2) {
    return
  }
  activeForm.value++
}
function prev() {
  if (activeForm.value <= 0) {
    return
  }
  activeForm.value--
}
function submit() {
  console.log('Email: ', email.value)
  console.log('Password: ', password.value)
  console.log('Phone Number: ', phone.value)
}
</script>

<template>
  <div class="wizard">
    <div v-if="activeForm == 0" class="email-form">
      <label for="email">Enter your email:</label><br />
      <input v-model="email" type="text" name="email" placeholder="Email" style="margin-bottom: 16px;">

      <div>
        <button @click="next" :disabled="!email" style="margin-bottom: 16px;">Next</button>
      </div>
    </div>

    <div v-if="activeForm == 1" class="password-form">
      <label for="password">Enter your password:</label><br />
      <input v-model="password" type="password" name="password" placeholder="Password" style="margin-bottom: 16px;">

      <div>
        <button @click="prev" style="margin-bottom: 16px;margin-right: 16px;">Previous</button>
        <button @click="next" :disabled="!password" style="margin-bottom: 16px;">Next</button>
      </div>
    </div>

    <div v-if="activeForm == 2" class="phone-form">
      <label for="phone">Enter your phone number:</label><br />
      <input v-model="phone" type="phone" name="phone" placeholder="phone" style="margin-bottom: 16px;">

      <div>
        <button @click="prev" style="margin-bottom: 16px;margin-right: 16px;">Previous</button>
        <button @click="submit" :disabled="!phone" style="margin-bottom: 16px;">Register</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wizard {
  display: flex;
  width: 100%;
  height: 70vh;
  justify-content: center;
  align-items: center;
}
</style>
