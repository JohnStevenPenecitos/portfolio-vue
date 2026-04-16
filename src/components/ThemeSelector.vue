<script setup>
import { ref, onMounted } from "vue";

const theme = ref("dark");
const themeIcon = ref("fa-solid fa-sun");

const setTheme = (mode) => {
  theme.value = mode;
  if (mode === "dark") {
    document.documentElement.classList.add("dark"); 
  } else {
    document.documentElement.classList.remove("dark");
  }
  localStorage.setItem("theme", mode);
  themeIcon.value = mode === "dark" ? "fa-solid fa-moon" : "fa-solid fa-sun";
};

const toggleTheme = () => {
  setTheme(theme.value === "dark" ? "light" : "dark");
};

onMounted(() => {
  const savedTheme = localStorage.getItem("theme") || "dark";
  setTheme(savedTheme);
});
</script>

<template>
  <div class="fixed bottom-4 right-4 z-50">
    <div class="flex justify-end">
      <div
        @click="toggleTheme"
        class="flex justify-center items-center cursor-pointer md:p-3 p-2 rounded-full shadow-lg bg-white dark:bg-zinc-800 text-gray-800 dark:text-white duration-300"
      >
        <i :class="themeIcon" class="md:text-xl text-md"></i>
      </div>
    </div>
  </div>
</template>
