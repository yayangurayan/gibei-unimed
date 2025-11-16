<script setup>
// Placeholder untuk halaman Login/Register (WDD 8.0)
</script>

<template>
  <div class="bg-gibei-secondary">
    <div class="min-h-screen flex items-center justify-center py-24 px-4 sm:px-6 lg:px-8">
      <div 
        class="max-w-md w-full space-y-8 bg-white p-10 rounded-2xl shadow-2xl"
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :enter="{ opacity: 1, y: 0, transition: { type: 'spring', stiffness: 100, delay: 100 } }"
      >
        <div>
          <h2 class="text-center text-4xl font-poppins font-extrabold text-gibei-primary">
            Masuk ke Akun Anda
          </h2>
          <p class="mt-2 text-center text-base font-inter text-gibei-text">
            (Halaman Placeholder untuk WDD 8.0 - User Dashboard)
          </p>
        </div>
        <form class="mt-8 space-y-6" @submit.prevent>
          
          <div class="rounded-md shadow-sm -space-y-px">
            <div>
              <label for="email-address" class="sr-only">Alamat Email</label>
              <input id="email-address" name="email" type="email" required class="appearance-none rounded-t-lg relative block w-full px-4 py-3 border border-gray-300 placeholder-gray-500 text-gibei-text focus:outline-none focus:ring-gibei-primary focus:border-gibei-primary focus:z-10 sm:text-sm font-inter" placeholder="Alamat Email">
            </div>
            <div>
              <label for="password" class="sr-only">Password</label>
              <input id="password" name="password" type="password" required class="appearance-none rounded-b-lg relative block w-full px-4 py-3 border border-gray-300 placeholder-gray-500 text-gibei-text focus:outline-none focus:ring-gibei-primary focus:border-gibei-primary focus:z-10 sm:text-sm font-inter" placeholder="Password">
            </div>
          </div>

          <div class="flex items-center justify-between">
            <div class="text-sm">
              <a href="#" class="font-medium font-inter text-gibei-primary hover:text-blue-800">
                Lupa password?
              </a>
            </div>
          </div>

          <div>
            <button type="submit" class="group relative w-full flex justify-center py-3 px-4 border border-transparent text-sm font-poppins font-medium rounded-lg text-white bg-gibei-primary hover:bg-blue-900 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gibei-primary transition duration-300">
              Masuk
            </button>
          </div>
        </form>
        
        <p class="text-center text-sm font-inter text-gibei-text">
          Belum punya akun? 
          <a href="#" class="font-medium text-gibei-primary hover:text-blue-800">
            Daftar di sini
          </a>
        </p>
      </div>
    </div>
  </div>
</template>