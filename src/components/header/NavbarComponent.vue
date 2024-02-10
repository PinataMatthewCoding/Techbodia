<template>
  <div class="navbar sticky top-0 lg:mx-20 md:mx-10 mx-5">
    <nav class="p-4 bg-white lg:flex justify-between md:items-center border-gray-200 ">
      <div class="flex justify-between md:items-center md:flex justify-between">
        <span class="text-2xl font-[Poppins] cursor-pointer font-serif" style="font-size: 14px; font-family: 'Kantumruy Pro', sans-serif">
          <img class="h-12 inline " src="../../assets/logo.png"/>
        </span>
        <span class="lg:hidden md:block md:mr-10 text-4xl cursor-pointer flex-end font-serif"  style="font-family: 'Kantumruy Pro', sans-serif">
          <svg  class="md:w-9 md:h-9 w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15"></path>
          </svg>
          <svg class="w-6 h-6 text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
          </svg>
        </span>
      </div>
      <h1 class="font-bold text-xl">Countries Catalog Implementation</h1>
      <!-- Navbar Left -->
      <div class="form-search">
        <form class="flex items-center w-80">
          <div class="relative w-full">
            <input v-model="searchQuery" type="text" id="simple-search" class="w-80 text-sm block border-gray-500 border-2 p-2 rounded-lg" placeholder="Search by country name" required>
          </div>
        </form>
      </div>
    </nav>
  </div>
</template>