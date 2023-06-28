
<template>
    <section v-if="false" class="fixed w-full left-0 top-0 h-screen z-50 bg-black flex flex-col justify-center items-center">

        <h1 data-aos="fade-up" class="tangerine-font text-2xl text-white">Undangan Pernikahan</h1>
        
        <div data-aos="fade-up" class="w-44 h-44 mt-5 mb-2 rounded-full overflow-hidden flex justify-center items-center outline outline-2 outline-white">
            <img src="../../public/galleries/a6.jpg" alt="">
        </div>

        <decoration data-aos="fade-up" class="fill-amber-400 mx-auto w-3/12 lg:w-1/12"></decoration>
        <p data-aos="fade-up" class="text-sm flex flex-col justify-center text-gray-100 text-center">
          <p class="font-medium">Kepada Bapak/Ibu Yang Terhormat</p>
          <p class="my-2 text-lg font-bold">{{ query.to }}</p>
          <small>Izinkan kami turut mengundang anda dalam acara kami</small>
        </p>

        <button data-aos="fade-up" class="mt-3 border border-white px-2 py-1 rounded-md text-white hover:bg-white duration-300 hover:text-black">Buka Undangan</button>

    </section>
</template>

<script setup>

const tutupUndangan = defineEmits(['tutup'])

// import { ref } from 'vue'
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import decoration from '@/assets/svg/decoration-2.svg'

const route = useRoute()
let query = computed(() => route.query)

if ( route.query.to === undefined ) query = { to: 'Saudara/i' }

let showUndangan = {
    type: Boolean,
    default: false
}

</script>

