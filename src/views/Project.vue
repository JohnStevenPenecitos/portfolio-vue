<template>
  <div class="min-h-screen text-white px-6 py-14 md:px-12">
    <div
      class="flex flex-col md:flex-row justify-between items-end mb-10 gap-6"
    >
      <div class="max-w-2xl mt-10">
        <div class="flex items-center gap-2 mb-4 text-primary font-medium">
          <Sparkles class="w-5 h-5" />
          <span>Selected Works</span>
        </div>

        <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-4">
          From Concept <br />
          <span
            class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-accent"
          >
            To Working Product
          </span>
        </h2>

        <p class="text-lg text-muted-foreground leading-relaxed">
          A curated selection of projects where ideas were translated into
          functional, user-focused applications.
        </p>
      </div>
    </div>

    <div
      class="flex items-center gap-2 bg-zinc-900 border border-zinc-800 rounded-2xl p-1.5 max-w-lg mb-15"
    >
      <button
        v-for="tab in tabs"
        :key="tab.id"
        @click="setTab(tab.id)"
        :class="[
          'flex-1 flex items-center justify-center gap-2 px-4 py-3 rounded-xl text-sm font-bold transition-all duration-300',
          activeTab === tab.id
            ? 'bg-zinc-800 text-white border border-zinc-700 shadow-lg'
            : 'text-zinc-500 hover:text-zinc-300',
        ]"
      >
        <span class="text-base">{{ tab.icon }}</span>
        <span class="hidden sm:inline">{{ tab.label }}</span>

        <span
          :class="[
            'text-xs font-bold px-2 py-0.5 rounded-full transition-all duration-300',
            activeTab === tab.id
              ? 'bg-primary text-white'
              : 'bg-muted text-muted-foreground hover:bg-muted/70',
          ]"
        >
          {{ tab.projects.length }}
        </span>
      </button>
    </div>

    <div
      :key="activeTab"
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5"
    >
      <ProjectCard
        v-for="(project, i) in currentProjects"
        :key="project.id"
        :project="project"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

import ProjectCard, { Project } from "@/components/cards/ProjectCard.vue";
import { Sparkles } from "lucide-vue-next";

import ecrsImg from "@/assets/system-ss/ECRS.png";
import ciebotImg from "@/assets/system-ss/CIEBOT.png";
import ilypImg from "@/assets/system-ss/ILYP.png";
import smsImg from "@/assets/system-ss/SMS.png";
import pokedexImg from "@/assets/system-ss/PokeDex.png";
import strkImg from "@/assets/system-ss/StreakCard.png";
import vrznImg from "@/assets/system-ss/Vrzn.png";
import n8ndtr from "@/assets/system-ss/dtr-n8n.png";


type Tab = {
  id: string;
  label: string;
  icon: string;
  projects: Project[];
};

const tabs = ref<Tab[]>([
  {
    id: "webdev",
    label: "Web Development",
    icon: "⬡",
    projects: [
      {
        id: 1,
        slug: "e-class",
        title: "E-Class Record System",
        shortDescription:
          "A digital platform for managing student grades and class records efficiently.",
        category: "Full Stack Development",
        image: ecrsImg,
        github: "https://github.com",
        demo: "",
        techStack: ["Laravel", "MySQL", "Tailwind CSS", "jQuery"],
        role: "Full Stack Developer",
        year: "2025",
      },
      {
        id: 2,
        slug: "ciebot",
        title: "CIEBOT",
        shortDescription:
          "An AI-powered chatbot that assists students with academic inquiries.",
        category: "Chat Bot",
        image: ciebotImg,
        github: "https://github.com",
        demo: "https://www.youtube.com/watch?v=2GLslF7Uz80",
        techStack: ["Vue.js", "OpenAI API", "Laravel", "Socket.io"],
        role: "Front End Developer",
        year: "2024",
      },
      {
        id: 3,
        slug: "let-pass",
        title: "ILetUPass",
        shortDescription:
          "A study aid designed to help students prepare for board exams.",
        category: "Full Stack Development",
        image: ilypImg,
        github: "https://github.com",
        demo: "https://youtu.be/xPVEq0lEK30",
        techStack: ["Vue.js", "Laravel", "MySQL", "Tailwind CSS"],
        role: "Full Stack Developer",
        year: "2023",
      },
      {
        id: 4,
        slug: "sanction",
        title: "Sanction Management System",
        shortDescription:
          "A system designed to track and manage disciplinary actions.",
        category: "Full Stack Development",
        image: smsImg,
        demo: "",
        techStack: ["Laravel", "MySQL", "Bootstrap"],
        role: "Full Stack Developer",
        year: "2023",
      },
      {
        id: 5,
        slug: "streak-card",
        title: "Streak Card",
        shortDescription: "A digital reward and loyalty tracking system.",
        category: "Marketing",
        image: strkImg,
        demo: "",
        techStack: ["Laravel", "MySQL", "Tailwind CSS"],
        role: "Full Stack Developer",
        year: "2024",
      },
      {
        id: 6,
        slug: "verizon",
        title: "Verizon Bank",
        shortDescription:
          "A modern banking platform offering secure transactions.",
        category: "Bank",
        image: vrznImg,
        demo: "",
        techStack: ["HTML", "CSS", "PHP"],
        role: "Full Stack Developer",
        year: "2024",
      },
      {
        id: 7,
        slug: "poke-dex",
        title: "PokeDex",
        shortDescription: "A comprehensive database for Pokémon enthusiasts.",
        category: "Side Project",
        image: pokedexImg,
        demo: "",
        techStack: ["HTML", "CSS", "JS", "PokeAPI"],
        role: "Full Stack Developer",
        year: "2023",
      },
    ],
  },
  {
    id: "automation",
    label: "Automation",
    icon: "◈",
    projects: [
      {
        id: 8,
        slug: "dtr-creator",
        title: "DTR Creator using Google Sheet Duplication",
        shortDescription:
          "Automated extraction of invoice data from PDFs and emails into a structured spreadsheet.",
        category: "Data Automation",
        image: n8ndtr,
        demo: "",
        techStack: ["Google Sheet API", "n8n"],
        role: "Automation Developer",
        year: "2024",
      },
    ],
  },
]);

const activeTab = ref<string>("webdev");

const currentProjects = computed<Project[]>(() => {
  return tabs.value.find((t) => t.id === activeTab.value)?.projects ?? [];
});

function setTab(id: string) {
  activeTab.value = id;
}
</script>
