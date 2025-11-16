<script setup>
import { useRoute } from 'vue-router'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

// 1. Impor `useRoute` untuk mendapatkan path URL saat ini
const route = useRoute()
</script>

<template>
  <Navbar />
  
  <main>
    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <!-- 
          PERBAIKAN KUNCI: 
          Menambahkan :key="route.path" akan MEMAKSA 
          Vue untuk me-mount ulang komponen halaman (cth: Home.vue)
          setiap kali Anda navigasi. Ini akan me-reset
          state v-motion dan memperbaiki bug halaman kosong.
        -->
        <component :is="Component" :key="route.path" />
      </transition>
    </router-view>
  </main>

  <Footer />
</template>

<style>
/* CSS global (termasuk .fade-*) ada di src/style.css */
</style>