<script setup>
import { ref } from "vue";
import TopNavbar from "./components/TopNavbar.vue";
import ThemeSelector from "./components/ThemeSelector.vue";

const blobs = ref([
  {
    id: 1,
    size: "500px",
    top: "10%",
    left: "20%",
    color: "rgba(173, 232, 213, 0.8)",
    duration: 8,
  },
  {
    id: 2,
    size: "550px",
    top: "40%",
    left: "65%",
    color: "rgba(192, 160, 255, 0.8)",
    duration: 10,
  },
  {
    id: 3,
    size: "500px",
    top: "70%",
    left: "10%",
    color: "rgba(255, 182, 193, 0.8)",
    duration: 12,
  },
  {
    id: 4,
    size: "500px",
    top: "0%",
    left: "70%",
    color: "rgba(255, 182, 250, 0.8)",
    duration: 14,
  },
]);
</script>

<template>
  <div
    class="relative flex flex-col p-3 font-display min-h-screen overflow-hidden"
  >
    <div
      class="fixed inset-0 overflow-hidden -z-10 pointer-events-none bg-[#f9f7f3] dark:bg-zinc-900"
    >
      <div
        v-for="blob in blobs"
        :key="blob.id"
        class="absolute rounded-full dark:blur-[100px] blur-[70px] opacity-70 will-change-transform"
        :style="{
          width: blob.size,
          height: blob.size,
          top: blob.top,
          left: blob.left,
          background: `radial-gradient(circle, ${blob.color} 0%, transparent 70%)`,
          transform: 'translate3d(0,0,0)',
          animation: `float-${blob.id} ${blob.duration}s ease-in-out infinite alternate`,
        }"
      />
    </div>
    <main
      class="gap-2 transition-all duration-300 flex flex-col flex-1 h-full items-center"
    >
      <TopNavbar />
      <div class="flex-1 lg:px-56 px-0 flex justify-center">
        <RouterView />
      </div>
    </main>
    <ThemeSelector />
  </div>
</template>
