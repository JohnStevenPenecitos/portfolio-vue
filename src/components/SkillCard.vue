<template>
  <div
    :class="cn(
      'flex flex-shrink-0 items-center justify-center rounded-lg bg-card px-8 py-6 shadow-sm transition-all',
      'hover:shadow-md hover:scale-105'
    )"
  >
    <div class="flex items-center space-x-3">

      <!-- Icon -->
      <div class="h-8 w-8 rounded bg-primary/10 flex items-center justify-center">
        <img
          v-if="skill.stackIcon"
          :src="skill.stackIcon"
          :alt="skill.name"
          class="w-6 h-6 object-cover"
        />
        <span v-else class="text-xs font-bold text-primary">
          {{ skill.name.substring(0, 2).toUpperCase() }}
        </span>
      </div>

      <!-- Name -->
      <span class="text-sm font-medium text-foreground whitespace-nowrap">
        {{ skill.name }}
      </span>

    </div>
  </div>
</template>

<script setup>
import { cn } from "@/lib/utils";

defineProps({
  skill: {
    type: Object,
    required: true,
  },
});
</script>