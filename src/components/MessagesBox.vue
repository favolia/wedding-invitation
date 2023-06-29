<template>
  <section class="w-10/12 mx-auto mt-6">
    <p>Ada {{ messages.length }} pesan dari para tamu</p>
  </section>
  <section style="max-height: 400px" class="w-10/12 mt-5 mx-auto overflow-scroll">
    <template v-for="(msg, x) in messages" :key="x">
      <div class="w-full mb-5 border-b-2 border-green-200 pb-1">
        <span class="flex gap-2 items-center">
          <p class="kalam-font text-green-500 text-xl">{{ msg.guestName }}</p>
          <span class="py-1 px-2 bg-gray-600 text-gray-100 rounded-lg text-xxs">{{ msg.guestStatus }}</span>
        </span>
        <p class="font-medium text-xs mt-2">Pada {{ moment.unix(msg.timestamp).format("D MMMM YYYY") }}</p>
        <p class="text-sm">{{ msg.guestMessage }}</p>
      </div>
    </template>
  </section>
</template>

<script setup>

import moment from 'moment'

const props = defineProps({
  messages: {
    type: Array
  }
})

</script>
