<script setup>
import { ref } from 'vue'
import { z } from 'zod'
import { Form } from '@primevue/forms'
import { zodResolver } from '@primevue/forms/resolvers/zod'
import { useToastNotifications } from '@/composables/useToastNotifications.js'
import Button from 'primevue/button'
import InputText from 'primevue/inputtext'
import Message from 'primevue/message'
import Toast from 'primevue/toast'
import { supabase } from '@/supabase.js'

const { showToast } = useToastNotifications()

const formData = ref({
  email: '',
  password: '',
  firstname: '',
})

const rules = z.object({
  firstname: z.string().min(1, { message: 'Имя обязательно заполнить' }),
  email: z.email({ message: 'Введён некорректный email' }),
  password: z.string().min(5, { message: 'Должно быть не менее 6 символов' }),
})

const resolver = zodResolver(rules)

const submitForm = async ({ valid }) => {
  if (!valid) {
    return
  } else {
    const { data, error } = await supabase.auth.signUp({
      email: formData.value.email,
      password: formData.value.password,
    })

    if (error) {
      showToast('error', 'Ошибка регистрации', error)
    } else {
      showToast('success', 'Регистрация', 'Вы успешно зарегистрировались')
    }
  }

  console.log(valid)
}
</script>

<template>
  <Toast />
  <Form
    v-slot="$form"
    :initial-values="formData"
    :resolver="resolver"
    :validate-on-blur="true"
    :validate-on-value-update="false"
    @submit="submitForm"
  >
    <div class="mb-3">
      <InputText
        name="email"
        placeholder="введите email"
        type="text"
        v-model="formData.email"
        class="w-full"
      />
      <Message v-if="$form.email?.invalid" severity="error" variant="simple" size="small">
        {{ $form.email.error.message }}
      </Message>
    </div>
    <div class="mb-3">
      <InputText
        name="password"
        placeholder="введите пароль"
        type="password"
        v-model="formData.password"
        class="w-full"
      />
      <Message v-if="$form.password?.invalid" severity="error" variant="simple" size="small">
        {{ $form.password.error.message }}
      </Message>
    </div>
    <div class="mb-3">
      <InputText
        name="firstname"
        placeholder="введите свое имя"
        type="text"
        v-model="formData.firstname"
        class="w-full"
      />
      <Message v-if="$form.firstname?.invalid" severity="error" variant="simple" size="small">
        {{ $form.firstname.error.message }}
      </Message>
    </div>
    <div class="grid grid-cols-2 gap-3">
      <Button type="submit" class="w-full bg-[#2563EB]" label="Регистрация" />
      <Button type="submit" icon="pi pi-github" class="w-full" label="Github" severity="contrast" />
    </div>
  </Form>
</template>
