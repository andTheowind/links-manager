<script setup>
import 'primeicons/primeicons.css'
</script>
<template>
  <main>
    <div class="flex flex-col lg:flex-row items-center max-w-7xl mx-auto gap-6 h-screen">
      <div class="order-1 lg:order-1">
        <h1 class="text-3xl font-bold text-black mb-1 max-w-[18rem]">
          Ваши ссылки — всегда под рукой
        </h1>
        <p class="text-gray-600 text-base mb-6 max-w-[22rem]">
          Сохраняйте, организовывайте и быстро находите нужные ссылки в одном месте.
        </p>
        <a
          href="/auth"
          class="flex flex-row justify-center bg-[#34d399] max-w-full lg:max-w-[fit] rounded-lg px-4 py-3 gap-3"
        >
          <i class="pi pi-sign-in text-lg inline-block pt-1 text-black"></i>
          <div class="flex">
            <span class="font-medium text-sm text-black">К входу</span>
          </div>
        </a>
      </div>
      <div class="order-0 lg:order-1">
        <img
          src="@/assets/img/Gemini_Generated_Image_3x4upc3x4upc3x4u-removebg-preview.png"
          alt=""
        />
      </div>
    </div>
  </main>
</template>

<style scoped></style>
