<template>
  <img v-motion-fade-visible
    :src="icon"
    class="p-2 mt-2 flex items-center justify-center h-28"
    alt="icon"
    v-if="icon"
  />
</template>

<script setup>
import { defineProps } from "vue";

defineProps({
  icon: {
    type: String,
    required: true,
  },
});
</script>
