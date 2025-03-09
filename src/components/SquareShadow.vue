<template>
    <div class="flex items-center justify-center bg-white">
      <div
        :class="['relative bg-white dark:bg-zinc-900 shadow-[8px_8px_0px_rgba(0,0,0,1)] flex items-center justify-center', size]"
      >
        <slot></slot>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from "vue";
  
  defineProps({
    size: {
      type: String,
      default: "",
    },
  });
  </script>
  