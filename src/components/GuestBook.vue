<style scoped>

.frame {
  @apply w-4/12 rotate-180;
}

.input-wrapper {
  @apply w-full flex flex-wrap gap-1 mb-3;
}

label {
  @apply w-full text-gray-600 font-medium;
}

input, textarea, select, option {
  @apply w-full px-2 py-3 rounded-lg bg-gray-800 border border-gray-100 shadow-lg duration-300 focus:border-gray-500 text-gray-200 placeholder:text-gray-400;
}

</style>

<template>
  <section class="w-full bg-slate-100 pt-5">
    <section class="container-section bg-slate-100">
      <HeaderSection
        title="Buku Tamu"
        subtitle="Demi kelancaran acara dimohon untuk para tamu undangan untuk memastikan kehadirannya pada acara kami"
      />
      <!-- Form -->
      <form ref="form" @submit="sendMessage" class="w-10/12 mx-auto mt-6">
        <!-- Guest Name -->
        <div class="input-wrapper" data-aos="zoom-in">
          <label for="GuestName">Nama</label>
          <input
            v-model="GuestName"
            placeholder="Nama lengkap anda"
            name="GuestName"
            id="GuestName"
            type="text"
            required
          />
        </div>
        <!-- Guest Status -->
        <div class="input-wrapper" data-aos="zoom-in">
          <label for="GuestStatus">Kehadiran</label>
          <select v-model="GuestStatus" name="GuestStatus" id="GuestStatus" required>
            <option value="Hadir">Hadir</option>
            <option value="Tidak Hadir">Tidak Hadir</option>
          </select>
        </div>
        <!-- Guest Message -->
        <div class="input-wrapper" data-aos="zoom-in">
          <label for="GuestMessage">Pesan</label>
          <textarea
            placeholder="Tuliskan pesan anda disini"
            v-model="GuestMessage"
            name="GuestMessage"
            id="GuestMessage"
            cols="30"
            rows="5"
            required
          ></textarea>
        </div>
        <!-- Submit -->
        <button
          data-aos="zoom-in"
          class="w-full bg-gray-800 text-gray-100 mt-6 rounded-lg py-2 font-medium pointer active:scale-90 hover:border border-gray-500 hover:bg-gray-100 hover:text-green-500 duration-300"
          type="submit"
        >
          <i class="fa fa-paper-plane mr-1"></i>
          Kirim pesan
        </button>
        <!-- Alert -->
        <Alert class="mt-5"
          :statusResponse="statusResponse"
          :showAlert="showAlert"
          v-on:close="showAlert = false"
        />
      </form>
      <!-- Message Box -->
      <MessagesBox :messages="messages"></MessagesBox>
      <!-- Frames -->
      <div class="w-full text-center pb-12 mt-12">
        <p class="text-sm text-amber-600 font-medium"></p>
      </div>
    </section>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios';
import HeaderSection from '@/components/HeaderSection.vue';
import { useRoute } from 'vue-router'
import Alert from '@/components/Alert.vue';
import MessagesBox from '@/components/MessagesBox.vue';
import moment from "moment";

// Form handler
const form = ref(null);
const GuestName = ref(null);
const GuestMessage = ref(null);
const GuestStatus = ref('Hadir');

// Alert handler
const statusResponse = ref(false);
const showAlert = ref(false);

// URL
const scriptURL = 'https://wedding-36e5.restdb.io/rest/zul-wedding?apikey=649d581b8f786662ec82bfab';

const sendMessage = async (evt) => {
  evt.preventDefault();

  const payload = {
    guestName: GuestName.value,
    guestStatus: GuestStatus.value,
    guestMessage: GuestMessage.value,
    timestamp: moment().unix(),
  };

  try {
    const response = await axios.post(scriptURL, payload);
    console.log('Success:', response.data);
    statusResponse.value = true;
    showAlert.value = true;
  } catch (error) {
    console.error('Error:', error);
    statusResponse.value = false;
    showAlert.value = true;
  }
};

// Fetch messages from API
const fetchMessages = async () => {
  try {
    const response = await axios.get(scriptURL);
    return response.data;
  } catch (error) {
    console.error('Error:', error);
    throw error;
  }
};

const messages = ref([]);

fetchMessages().then((result) => {
  messages.value = result;
}).catch((error) => {
  console.error(error);
});

const route = useRoute()
if (route.query.to) {
  GuestName.value = route.query.to
}

</script>
