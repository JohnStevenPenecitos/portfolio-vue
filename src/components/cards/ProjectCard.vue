<template>
  <Card
    class="group h-full relative overflow-hidden rounded-[2rem] border-border/50 bg-card/60 backdrop-blur-md shadow-xl transition-all duration-300 hover:shadow-2xl hover:bg-card/80 hover:-translate-y-2 flex flex-col"
  >
    <div
      class="absolute -right-20 -top-20 h-40 w-40 rounded-full bg-primary/10 blur-3xl transition-opacity group-hover:opacity-75 pointer-events-none"
    />

    <CardHeader class="p-2 pb-0">
      <div class="relative aspect-video overflow-hidden rounded-[1.5rem]">
        <div
          class="flex h-full w-full items-center justify-center bg-gradient-to-br from-primary/20 via-primary/5 to-transparent"
        >
          <img
            v-if="project.image"
            :src="project.image"
            :alt="project.title"
            class="absolute inset-0 h-full w-full object-cover"
            loading="lazy"
          />
          <p
            v-else
            class="text-center text-sm text-muted-foreground/80 font-medium"
          >
            Project Preview<br />
            <span class="text-xs opacity-70">{{ project.title }}</span>
          </p>
        </div>

        <div
          class="absolute inset-0 bg-black/40 backdrop-blur-[2px] opacity-0 transition-opacity duration-300 group-hover:opacity-100 flex items-center justify-center gap-4 z-20"
        >
          <button
            class="transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300"
            @click.stop="showModal = true"
          >
            <div
              class="flex px-4 py-2 text-sm font-medium items-center justify-center rounded-full bg-secondary text-secondary-foreground shadow-lg hover:scale-105 transition-transform"
            >
              Details
            </div>
          </button>
        </div>

        <div class="absolute right-3 top-3 z-10">
          <span
            class="inline-flex items-center rounded-full border-0 bg-background/90 backdrop-blur-sm shadow-sm px-2.5 py-0.5 text-xs font-medium text-foreground"
          >
            {{ project.category }}
          </span>
        </div>
      </div>
    </CardHeader>

    <CardContent class="p-6 flex-grow flex flex-col">
      <div class="flex items-start justify-between gap-2 mb-3">
        <RouterLink :to="`/projects/${project.slug}`" class="flex-1">
          <CardTitle
            class="text-xl font-bold text-foreground group-hover:text-primary transition-colors inline-block hover:underline"
          >
            {{ project.title }}
          </CardTitle>
        </RouterLink>
      </div>

      <CardDescription
        class="mb-6 text-sm text-foreground/80 line-clamp-2 leading-relaxed"
      >
        {{ project.shortDescription }}
      </CardDescription>

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

    <CardFooter
      v-if="project.role || project.year"
      class="px-6 py-4 border-t border-border/50 flex items-center justify-between text-xs font-medium text-muted-foreground"
    >
      <span v-if="project.role">{{ project.role }}</span>
      <span v-if="project.year" class="opacity-70">{{ project.year }}</span>
    </CardFooter>
    <Teleport to="body">
      <Transition name="modal">
        <div
          v-if="showModal"
          class="fixed inset-0 z-50 flex items-center justify-center bg-black/60 backdrop-blur-sm p-4"
          @click.self="showModal = false"
        >
          <div
            class="relative w-full max-w-3xl bg-background rounded-[1.5rem] overflow-hidden shadow-2xl border border-border/50"
          >
            <div
              class="flex items-center justify-between px-6 py-4 border-b border-border/50"
            >
              <div>
                <h2 class="text-lg font-bold text-foreground">
                  {{ project.title }}
                </h2>
                <p class="text-xs text-muted-foreground">
                  {{ project.category }} · {{ project.year }}
                </p>
              </div>
              <button
                class="flex items-center justify-center w-8 h-8 rounded-full hover:bg-muted transition-colors text-muted-foreground hover:text-foreground"
                @click="showModal = false"
              >
                <XIcon class="w-4 h-4" />
              </button>
            </div>

            <div class="relative w-full aspect-video bg-black">
              <iframe
                v-if="hasDemo(project)"
                :src="project.demo"
                :title="`${project.title} demo`"
                class="w-full h-full border-0"
                allowfullscreen
                allow="autoplay; fullscreen"
              />

              <div v-else class="relative w-full h-full">
                <img
                  v-if="project.image"
                  :src="project.image"
                  :alt="project.title"
                  class="w-full h-full object-cover"
                />

                <div
                  v-else
                  class="flex items-center justify-center h-full text-muted-foreground"
                >
                  No preview available
                </div>
              </div>
            </div>
            <div class="px-6 py-4 border-t border-border/50">
              <p class="text-sm text-foreground/80 mb-3">
                {{ project.shortDescription }}
              </p>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="(tech, i) in project.techStack"
                  :key="i"
                  class="inline-flex items-center rounded-full border border-primary/20 bg-primary/5 px-2.5 py-0.5 text-xs font-medium text-foreground"
                >
                  {{ tech }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </Card>
</template>

<script setup lang="ts">
import {
  ExternalLink as ExternalLinkIcon,
  Github as GithubIcon,
  ArrowUpRight as ArrowUpRightIcon,
} from "lucide-vue-next";
import CardHeader from "./CardHeader.vue";
import CardContent from "./CardContent.vue";
import CardTitle from "./CardTitle.vue";
import CardFooter from "./CardFooter.vue";
import Card from "./Card.vue";
import { ref, watch } from "vue";

const showModal = ref(false);

const hasDemo = (project: Project) => {
  return !!project.demo && project.demo.trim() !== "";
};

watch(showModal, (val) => {
  document.body.style.overflow = val ? "hidden" : "";
});

export interface Project {
  id: number;
  slug: string;
  title: string;
  shortDescription: string;
  category: string;
  image?: string;
  github?: string;
  demo?: string;
  techStack: string[];
  role?: string;
  year?: string;
}

defineProps<{ project: Project }>();
</script>

<style scoped>
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.2s ease;
}
.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}
</style>
