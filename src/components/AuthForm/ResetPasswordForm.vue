<script setup>
import { ref } from 'vue'
import Button from 'primevue/button'
import InputText from 'primevue/inputtext'

const formData = ref({
  email: '',
})
</script>

<template>
  <form action="">
    <div class="mb-3">
      <InputText
        name="email"
        placeholder="введите email"
        type="text"
        v-model="formData.email"
        class="w-full"
      />
    </div>
    <div class="grid">
      <Button type="submit" class="w-full" label="Сброс пароля" />
    </div>
  </form>
</template>
