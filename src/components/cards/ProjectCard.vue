<template>
  <Card
    class="group h-full relative overflow-hidden rounded-[2rem] border-border/50 bg-card/60 backdrop-blur-md shadow-xl transition-all duration-300 hover:shadow-2xl hover:bg-card/80 hover:-translate-y-2 flex flex-col"
  >
    <div class="absolute -right-20 -top-20 h-40 w-40 rounded-full bg-primary/10 blur-3xl transition-opacity group-hover:opacity-75 pointer-events-none" />

    <CardHeader class="p-2 pb-0">
      <div class="relative aspect-video overflow-hidden rounded-[1.5rem]">
        <div class="flex h-full w-full items-center justify-center bg-gradient-to-br from-primary/20 via-primary/5 to-transparent">
          <img
            v-if="project.image"
            :src="project.image"
            :alt="project.title"
            class="absolute inset-0 h-full w-full object-cover"
            loading="lazy"
          />
          <p v-else class="text-center text-sm text-muted-foreground/80 font-medium">
            Project Preview<br />
            <span class="text-xs opacity-70">{{ project.title }}</span>
          </p>
        </div>

        <!-- Hover overlay -->
        <div
          class="absolute inset-0 bg-black/40 backdrop-blur-[2px] opacity-0 transition-opacity duration-300 group-hover:opacity-100 flex items-center justify-center gap-4 z-20"
        >
          <RouterLink
            :to="`/projects/${project.slug}`"
            class="transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300"
          >
            <div class="flex px-4 py-2 text-sm font-medium items-center justify-center rounded-full bg-secondary text-secondary-foreground shadow-lg hover:scale-105 transition-transform">
              Details
            </div>
          </RouterLink>

          <a
            v-if="project.github"
            :href="project.github"
            target="_blank"
            rel="noopener noreferrer"
            class="transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300 delay-75"
            @click.stop
          >
            <div class="flex h-12 w-12 items-center justify-center rounded-full bg-white text-black shadow-lg hover:scale-110 transition-transform">
              <GithubIcon class="h-5 w-5" />
            </div>
          </a>

          <a
            v-if="project.demo"
            :href="project.demo"
            target="_blank"
            rel="noopener noreferrer"
            class="transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300 delay-100"
            @click.stop
          >
            <div class="flex h-12 w-12 items-center justify-center rounded-full bg-primary text-primary-foreground shadow-lg hover:scale-110 transition-transform">
              <ExternalLinkIcon class="h-5 w-5" />
            </div>
          </a>
        </div>

        <!-- Category badge -->
        <div class="absolute right-3 top-3 z-10">
          <span class="inline-flex items-center rounded-full border-0 bg-background/90 backdrop-blur-sm shadow-sm px-2.5 py-0.5 text-xs font-medium text-foreground">
            {{ project.category }}
          </span>
        </div>
      </div>
    </CardHeader>

    <CardContent class="p-6 flex-grow flex flex-col">
      <div class="flex items-start justify-between gap-2 mb-3">
        <RouterLink :to="`/projects/${project.slug}`" class="flex-1">
          <CardTitle class="text-xl font-bold text-foreground group-hover:text-primary transition-colors inline-block hover:underline">
            {{ project.title }}
          </CardTitle>
        </RouterLink>
        <a
          v-if="project.demo"
          :href="project.demo"
          target="_blank"
          rel="noopener noreferrer"
        >
          <ArrowUpRightIcon class="h-5 w-5 text-muted-foreground opacity-0 -translate-x-2 group-hover:opacity-100 group-hover:translate-x-0 transition-all duration-300 hover:text-primary" />
        </a>
      </div>

      <CardDescription class="mb-6 text-sm text-foreground/80 line-clamp-2 leading-relaxed">
        {{ project.shortDescription }}
      </CardDescription>

      <!-- Tech Stack -->
      <div class="flex flex-wrap gap-2 mb-4 mt-auto">
        <span
          v-for="(tech, i) in project.techStack"
          :key="i"
          class="inline-flex items-center rounded-full border border-primary/20 bg-primary/5 hover:bg-primary/10 transition-colors px-2.5 py-0.5 text-xs font-medium text-foreground"
        >
          {{ tech }}
        </span>
      </div>
    </CardContent>

    <!-- Footer -->
    <CardFooter
      v-if="project.role || project.year"
      class="px-6 py-4 border-t border-border/50 flex items-center justify-between text-xs font-medium text-muted-foreground"
    >
      <span v-if="project.role">{{ project.role }}</span>
      <span v-if="project.year" class="opacity-70">{{ project.year }}</span>
    </CardFooter>
  </Card>
</template>

<script setup lang="ts">
import { ExternalLink as ExternalLinkIcon, Github as GithubIcon, ArrowUpRight as ArrowUpRightIcon } from 'lucide-vue-next'
import CardHeader from './CardHeader.vue'
import CardContent from './CardContent.vue'
import CardTitle from './CardTitle.vue'
import CardFooter from './CardFooter.vue'
import Card from './Card.vue'


export interface Project {
  slug: string
  title: string
  shortDescription: string
  category: string
  image?: string
  github?: string
  demo?: string
  techStack: string[]
  role?: string
  year?: string
}

defineProps<{ project: Project }>()
</script>