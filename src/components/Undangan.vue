<template>
    <section v-if="showUndangan" class="fixed w-full left-0 top-0 h-screen z-50 bg-black flex flex-col justify-center items-center">
      <h1 class="tangerine-font text-2xl text-white" data-aos="fade-up">Undangan Pernikahan</h1>
      
      <div class="w-44 h-44 mt-5 mb-2 rounded-full overflow-hidden flex justify-center items-center outline outline-white" data-aos="fade-up">
        <img src="/galleries/a6.jpg" alt="">
      </div>
  
      <decoration class="fill-amber-400 mx-auto w-3/12 lg:w-1/12" data-aos="fade-up"></decoration>
      <p class="text-sm flex flex-col justify-center text-gray-100 text-center" data-aos="fade-up">
        <p class="font-medium">Kepada Bapak/Ibu Yang Terhormat</p>
        <p class="my-2 text-lg font-bold">{{ query.to }}</p>
        <small>Izinkan kami turut mengundang anda dalam acara kami</small>
      </p>
  
      <button class="mt-3 border border-white px-2 py-1 rounded-md text-white hover:bg-white duration-300 hover:text-black" @click="hideUndangan">Buka Undangan</button>
    </section>
  </template>
  
  <script setup>
  import { computed, ref, onMounted } from 'vue'
  import { useRoute } from 'vue-router'
  import decoration from '@/assets/svg/decoration-2.svg'
  
  const route = useRoute()
  let query = computed(() => route.query)
  
  if (route.query.to === undefined) query = { to: 'Saudara/i' }
  
  const showUndangan = ref(true)
  
  const hideUndangan = () => {
    showUndangan.value = false
    document.body.style.overflow = 'auto'
  }
  
  onMounted(() => {
    document.body.style.overflow = 'hidden'
  })
  </script>
  