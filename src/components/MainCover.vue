<template>
  <section class="w-full bg-couples bg-cover h-screen">
    <section class="container-section h-screen grid content-end">
      <div 
        class="animate__animated animate__fadeInUpBig text-gray-100 text-center bg-gray-800 bg-opacity-50 backdrop-blur-sm rounded-t-3xl px-6 py-10">
        <p>Pernikahan</p>
        <h1 class="tangerine-font text-title sm:text-4xl font-bold">{{ couples[0] }}</h1>
        <sup class="font-serif font-normal text-lg">(Zul)</sup>
        <h1 class="tangerine-font text-title leading-[3rem]">&</h1>
        <h1 class="tangerine-font text-title sm:text-4xl font-bold">{{ couples[1] }}</h1>
        <sup class="font-serif font-normal text-lg">(Amel)</sup>
        <decoration class="fill-amber-400 mx-auto w-3/12 mb-3"></decoration>
        <p class="text-sm">
          <p class="font-medium">Kepada Bapak/Ibu Yang Terhormat</p>
          <p class="my-2 text-lg font-bold">{{ query.to }}</p>
          <small>Izinkan kami turut mengundang anda dalam acara kami</small>
        </p>
      </div>
    </section>
  </section>
</template>

<script setup>

import { computed } from 'vue'
import { useRoute } from 'vue-router'
import decoration from '@/assets/svg/decoration-2.svg'

const couples = ['Amirul Haj Adhi ', 'Putri Amelia Yusdar']

const route = useRoute()
let query = computed(() => route.query)

if ( route.query.to === undefined ) query = { to: 'Saudara/i' }

</script>
