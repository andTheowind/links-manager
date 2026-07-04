<script setup>
import { ref } from 'vue'
import { z } from 'zod'
import { Form } from '@primevue/forms'
import { zodResolver } from '@primevue/forms/resolvers/zod'
import Button from 'primevue/button'
import InputText from 'primevue/inputtext'
import Message from 'primevue/message'

const formData = ref({
  email: '',
})

const rules = z.object({
  email: z.email({ message: 'Введён некорректный email' }),
})

const resolver = zodResolver(rules)

const submitForm = async ({ valid }) => {
  console.log(valid)
}
</script>

<template>
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
    <div class="grid">
      <Button type="submit" class="w-full" label="Сброс пароля" />
    </div>
  </Form>
</template>
