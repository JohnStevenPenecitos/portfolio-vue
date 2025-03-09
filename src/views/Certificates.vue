<script setup>
import { ref } from "vue";

const blobs = ref([
  { id: 1, size: "300px", top: "20%", left: "25%", color: "rgba(173, 232, 213, 0.8)" }, // Soft green
  { id: 2, size: "350px", top: "50%", left: "60%", color: "rgba(192, 160, 255, 0.8)" }, // Soft purple
  { id: 3, size: "400px", top: "70%", left: "30%", color: "rgba(255, 182, 193, 0.8)" }, // Soft pink
]);
</script>

<template>
  <div class="relative w-full h-screen overflow-hidden bg-white">
    <div
      v-for="blob in blobs"
      :key="blob.id"
      class="absolute rounded-full blur-[40px] opacity-70"
      :style="{
        width: blob.size,
        height: blob.size,
        top: blob.top,
        left: blob.left,
        background: `radial-gradient(circle, ${blob.color} 0%, transparent 80%)`,
      }"
      v-motion
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
</template>
