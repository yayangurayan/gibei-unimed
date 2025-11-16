<script setup>
import { ref } from 'vue'

// Logika untuk mendapatkan bulan dan tahun saat ini
const currentDate = ref(new Date())
const currentMonth = computed(() => currentDate.value.toLocaleString('id-ID', { month: 'long' }))
const currentYear = computed(() => currentDate.value.getFullYear())

// Placeholder untuk hari-hari dalam sebulan (ini murni UI)
// Kita buat grid 7 kolom
const daysOfWeek = ['Sen', 'Sel', 'Rab', 'Kam', 'Jum', 'Sab', 'Min']
// Membuat 35 kotak (5 baris) untuk kalender
const calendarDays = ref(Array.from({ length: 35 }, (_, i) => i + 1))

// Placeholder event (UI)
const events = ref([
  { day: 10, title: 'Webinar' },
  { day: 17, title: 'SPM L1' },
  { day: 25, title: 'Workshop' },
])

const isEventDay = (day) => {
  return events.value.some(e => e.day === day)
}

const getEventTitle = (day) => {
  return events.value.find(e => e.day === day)?.title
}

// Logika simpel untuk 'grey out' (kita asumsikan 1-30)
const isCurrentMonth = (day) => {
  return day <= 30 // Asumsi bulan ini 30 hari
}

</script>

<template>
  <!-- 
    Komponen UI Kalender (WDD 3.2)
    Fokus 100% pada Frontend (Vibe "Elegan")
  -->
  <div
    class="bg-white p-6 md:p-8 rounded-lg shadow-xl overflow-hidden"
    v-motion
    :initial="{ opacity: 0, y: 50 }"
    :visibleOnce="{ opacity: 1, y: 0, transition: { type: 'spring', stiffness: 100, delay: 200 } }"
  >
    <!-- Header Kalender -->
    <div class="flex justify-between items-center mb-6">
      <h3 class="font-poppins text-2xl font-bold text-gibei-primary">
        {{ currentMonth }} {{ currentYear }}
      </h3>
      <!-- Navigasi (UI Saja) -->
      <div class="flex space-x-2">
        <button class="w-10 h-10 flex items-center justify-center rounded-full text-gibei-primary bg-gibei-secondary hover:bg-opacity-70 transition-colors">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
        </button>
        <button class="w-10 h-10 flex items-center justify-center rounded-full text-gibei-primary bg-gibei-secondary hover:bg-opacity-70 transition-colors">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
        </button>
      </div>
    </div>

    <!-- Grid Kalender -->
    <div>
      <!-- Nama Hari -->
      <div class="grid grid-cols-7 gap-2 mb-3">
        <div
          v-for="day in daysOfWeek"
          :key="day"
          class="font-poppins font-semibold text-center text-gibei-primary text-sm uppercase"
        >
          {{ day }}
        </div>
      </div>
      
      <!-- Tanggal -->
      <div class="grid grid-cols-7 gap-2">
        <div
          v-for="day in calendarDays"
          :key="day"
          :class="[
            'h-20 md:h-24 rounded-lg p-2 flex flex-col transition-all duration-300 border',
            isCurrentMonth(day) ? 'bg-white border-gray-200' : 'bg-gray-50 border-gray-100 text-gray-400',
            isEventDay(day) ? 'bg-gibei-secondary border-gibei-primary shadow-md' : ''
          ]"
        >
          <!-- Nomor Tanggal -->
          <span class="font-inter font-semibold">{{ isCurrentMonth(day) ? day : (day - 30) }}</span>
          
          <!-- Event (jika ada) -->
          <div v-if="isEventDay(day)" class="mt-1 text-xs font-poppins font-medium bg-gibei-primary text-white rounded px-1.5 py-0.5 text-center overflow-hidden whitespace-nowrap text-ellipsis">
            {{ getEventTitle(day) }}
          </div>
        </div>
      </div>
    </div>

  </div>
</template>