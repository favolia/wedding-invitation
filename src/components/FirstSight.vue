<template>
  <section class="w-full mb-12">
    <wave class="fill-orange-300"></wave>
    <section class="container-section">
      <HeaderSection title="Quotes"></HeaderSection>
      <Card title="Kisah kami berawal dari">
        <template v-slot:body>
          <p class="p-6 satisfy-font text-center text-2xl">
            " Bukan karena kita bertemu lalu kita jodoh, namun karena kita jodoh makanya dipertemukan. "
          </p>
        </template>
        <template v-slot:footer>
          <img src="/galleries/a3.jpg" class="w-full" alt="">
        </template>
      </Card>
    </section>
  </section>
</template>

<script setup>

import HeaderSection from '@/components/HeaderSection.vue'
import Card from '@/components/Card.vue'
import wave from '@/assets/svg/wave.svg'

</script>
