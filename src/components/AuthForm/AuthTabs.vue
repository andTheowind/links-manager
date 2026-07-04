<script setup>
import { ref } from 'vue'
import Tabs from 'primevue/tabs'
import TabList from 'primevue/tablist'
import Tab from 'primevue/tab'
import TabPanels from 'primevue/tabpanels'
import TabPanel from 'primevue/tabpanel'
import LoginForm from '@/components/AuthForm/LoginForm.vue'
import RegistrationForm from '@/components/AuthForm/RegistrationForm.vue'
import ResetPasswordForm from '@/components/AuthForm/ResetPasswordForm.vue'

const activeTab = ref('singin') // signin | signup | reset
</script>

<template>
  <Tabs v-model:value="activeTab">
    <TabList>
      <Tab value="singin">Вход</Tab>
      <Tab value="singup">Регистрация</Tab>
    </TabList>
    <TabPanels>
      <TabPanel value="singin">
        <LoginForm @resetPassword="activeTab = 'reset'" />
      </TabPanel>
      <TabPanel value="singup">
        <RegistrationForm />
      </TabPanel>
      <TabPanel value="reset">
        <ResetPasswordForm />
      </TabPanel>
    </TabPanels>
  </Tabs>
</template>
