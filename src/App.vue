<script setup>
import { ref } from "vue";
import TopNavbar from "./components/TopNavbar.vue";
import ThemeSelector from "./components/ThemeSelector.vue";

const blobs = ref([
  { id: 1, size: "500px", top: "10%", left: "20%", color: "rgba(173, 232, 213, 0.8)" }, 
  { id: 2, size: "550px", top: "40%", left: "65%", color: "rgba(192, 160, 255, 0.8)" }, 
  { id: 3, size: "500px", top: "70%", left: "30%", color: "rgba(255, 182, 193, 0.8)" }, 
]);


</script>

<template>
  <div class="relative flex flex-col p-3 font-display min-h-screen overflow-hidden light">
    <div class="absolute inset-0 overflow-hidden -z-10 bg-[#f9f7f3] dark:bg-zinc-900">
      <div
        v-for="blob in blobs"
        :key="blob.id"
        class="absolute rounded-full blur-[100px] opacity-70 "
        :style="{
          width: blob.size,
          height: blob.size,
          top: blob.top,
          left: blob.left,
          background: `radial-gradient(circle, ${blob.color} 0%, transparent 80%)`,
        }"
        :initial="{ opacity: 0.5, scale: 1 }"
        :animate="{
          opacity: 0.8,
          scale: [1, 1.1, 1],
          x: [0, Math.random() * 30 - 15],
          y: [0, Math.random() * 30 - 15],
        }"
        :transition="{
          duration: Math.random() * 5 + 5, 
          repeat: Infinity,
          repeatType: 'reverse',
          ease: 'easeInOut',
        }"
      />
    </div>
    <main class="gap-2 transition-all duration-300 flex flex-col flex-1 h-full items-center">
      <TopNavbar />
      <div class="flex-1 lg:px-56 px-0 flex justify-center">
        <RouterView />
      </div>
    </main>
    <ThemeSelector/>
  </div>
</template>
