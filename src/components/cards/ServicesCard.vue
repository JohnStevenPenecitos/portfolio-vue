<template>
  <div
    class="group p-8 rounded-3xl bg-background border border-border/50 hover:border-primary/50 transition-all hover:shadow-2xl hover:shadow-primary/5 relative overflow-hidden"
  >
    <div
      :class="[
        'absolute top-0 right-0 p-4 opacity-10 group-hover:opacity-20 transition-opacity',
        service.color,
      ]"
    >
      <component :is="service.icon" class="w-24 h-24" />
    </div>

    <div
      class="w-12 h-12 rounded-2xl bg-muted/50 flex items-center justify-center mb-6 text-primary group-hover:scale-110 transition-transform duration-300"
    >
      <component :is="service.icon" class="w-6 h-6" />
    </div>

    <h3 class="text-xl font-bold mb-3">{{ service.title }}</h3>
    <p class="text-muted-foreground leading-relaxed">
      {{ service.description }}
    </p>
  </div>
</template>

<script setup>
defineProps({
  service: {
    type: Object,
    required: true,
  },
});
</script>
