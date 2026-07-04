<script setup>
import { ref } from 'vue'
import Button from 'primevue/button'
import InputText from 'primevue/inputtext'

const formData = ref({
  email: '',
  password: '',
  firstname: '',
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
    <div class="mb-3">
      <InputText
        name="password"
        placeholder="введите пароль"
        type="password"
        v-model="formData.password"
        class="w-full"
      />
    </div>
    <div class="mb-3">
      <InputText
        name="firstname"
        placeholder="введите свое имя"
        type="text"
        v-model="formData.firstname"
        class="w-full"
      />
    </div>
    <div class="grid grid-cols-2 gap-3">
      <Button type="submit" class="w-full bg-[#2563EB]" label="Регистрация" />
      <Button type="submit" icon="pi pi-github" class="w-full" label="Github" severity="contrast" />
    </div>
  </form>
</template>
