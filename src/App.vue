<script setup>
import TopNavbar from "./components/TopNavbar.vue";
import Footer from "./components/Footer.vue";
</script>

<template>
  <div class="flex flex-col p-3 font-display min-h-screen overflow-auto bg-[#f9f7f3]">
    <main class="gap-2 transition-all duration-300 flex flex-col flex-1 h-full">
      <TopNavbar />
      <div class="flex-1  px-56 flex justify-center">
        <RouterView />
      </div>
    </main>
    <Footer />
  </div>
</template>
