<template>
  <div class="py-12 sm:w-full md:w-full w-[20rem] ">
    <div class="container mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mb-8 text-center">
        <h2 class="text-sm font-semibold uppercase tracking-widest text-muted-foreground">
          Powered By
        </h2>
      </div>

      <div
        :class="cn(
          'relative flex overflow-hidden mask-linear-gradient',
          pauseOnHover && 'group'
        )"
      >
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
        <div class="pointer-events-none absolute  w-20 from-background to-transparent z-10" />
        <div class="pointer-events-none absolute w-20 from-background to-transparent z-10" />
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
