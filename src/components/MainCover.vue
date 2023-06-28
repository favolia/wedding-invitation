<template>
  <section class="w-full bg-couples bg-cover bg-center h-[94vh]">
    <section class=" h-[94vh] flex items-end w-full">
      <div 
        class="animate__animated animate__fadeInUpBig h-[40%] w-full flex flex-col justify-center items-center text-gray-100 text-center bg-gray-800 bg-opacity-50 backdrop-blur-sm rounded-t-3xl px-6 py-32">
        <p class="mb-2">Akan Menikah</p>
        <h1 class="tangerine-font text-4xl font-bold">{{ couples[0] }}</h1>
        <sup class="font-serif font-normal text-lg">(Zul)</sup>
        <h1 class="tangerine-font text-title leading-[3rem]">&</h1>
        <h1 class="tangerine-font text-4xl font-bold">{{ couples[1] }}</h1>
        <sup class="font-serif font-normal text-lg">(Amel)</sup>
      </div>
    </section>
  </section>
</template>

<script setup>

import { computed } from 'vue'
import { useRoute } from 'vue-router'
// import decoration from '@/assets/svg/decoration-2.svg'

const couples = ['Amirul Haj Adhi ', 'Putri Amelia Yusdar']

const route = useRoute()
let query = computed(() => route.query)

if ( route.query.to === undefined ) query = { to: 'Saudara/i' }

</script>
