<template>
  <div class="py-12">
    <div class="container mx-auto max-w-5xl px-4 sm:px-6 lg:px-8 bg-red-200 ">

      <!-- Label -->
      <div class="mb-8 text-center">
        <h2 class="text-sm font-semibold uppercase tracking-widest text-muted-foreground">
          Powered By
        </h2>
      </div>

      <!-- Marquee Track -->
      <div
        :class="cn(
          'relative flex overflow-hidden mask-linear-gradient',
          pauseOnHover && 'group'
        )"
      >
        <!-- First Strip -->
        <div
          :class="cn(
            'flex min-w-full shrink-0 gap-8 animate-marquee items-center justify-around pr-8',
            pauseOnHover && 'group-hover:[animation-play-state:paused]'
          )"
          :style="{ animationDuration: `${speed}s` }"
        >
          <SkillCard
            v-for="(skill, index) in duplicatedSkills"
            :key="`1-${skill.name}-${index}`"
            :skill="skill"
          />
        </div>

        <!-- Second Strip (seamless loop) -->
        <div
          :class="cn(
            'flex min-w-full shrink-0 gap-8 animate-marquee items-center justify-around pr-8',
            pauseOnHover && 'group-hover:[animation-play-state:paused]'
          )"
          :style="{ animationDuration: `${speed}s` }"
        >
          <SkillCard
            v-for="(skill, index) in duplicatedSkills"
            :key="`2-${skill.name}-${index}`"
            :skill="skill"
          />
        </div>

        <!-- Fade Left -->
        <div class="pointer-events-none absolute inset-y-0 left-0 w-20 bg-red-400 from-background to-transparent z-10" />
        <!-- Fade Right -->
        <div class="pointer-events-none absolute inset-y-0 right-0 w-20 bg-red-500  from-background to-transparent z-10" />
      </div>

    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";
import { cn } from "@/lib/utils";
import SkillCard from "./SkillCard.vue";

const props = defineProps({
  skills: {
    type: Array,
    required: true,
  },
  speed: {
    type: Number,
    default: 200,
  },
  pauseOnHover: {
    type: Boolean,
    default: true,
  },
});

const duplicatedSkills = computed(() => [...props.skills, ...props.skills]);
</script>