<script setup lang="ts">
import Button from "@/components/Button.vue";
import CurveDivider from "@/components/CurveDivider.vue";
import { Sparkles } from "lucide-vue-next";

import ProjectCard, { Project } from "@/components/cards/ProjectCard.vue";

const projects: Project[] = [
  {
    slug: "luminary-cms",
    title: "Luminary CMS",
    shortDescription:
      "A headless CMS built for performance-obsessed teams — real-time collaboration, schema-first content modeling, and a blazing-fast API layer.",
    category: "Full Stack",
    image:
      "https://images.unsplash.com/photo-1555066931-4365d14bab8c?w=800&auto=format&fit=crop",
    github: "https://github.com",
    demo: "https://example.com",
    techStack: ["Nuxt 3", "TypeScript", "Supabase", "TailwindCSS"],
    role: "Lead Engineer",
    year: "2024",
  },
  {
    slug: "orbitui",
    title: "OrbitUI",
    shortDescription:
      "An accessible, themeable Vue component library with zero-runtime CSS, dark mode by default, and fully typed composables.",
    category: "Open Source",
    image:
      "https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=800&auto=format&fit=crop",
    github: "https://github.com",
    demo: "https://example.com",
    techStack: ["Vue 3", "Vite", "CSS Variables", "Vitest"],
    role: "Author & Maintainer",
    year: "2024",
  },
  {
    slug: "spectral-analytics",
    title: "Spectral Analytics",
    shortDescription:
      "Real-time event analytics dashboard with WebSocket ingestion, live charting, and anomaly detection powered by a lightweight ML pipeline.",
    category: "Data / ML",
    image:
      "https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800&auto=format&fit=crop",
    github: "https://github.com",
    techStack: ["Python", "FastAPI", "Vue 3", "Chart.js", "Redis"],
    role: "Solo Developer",
    year: "2023",
  },
  {
    slug: "driftmail",
    title: "DriftMail",
    shortDescription:
      "Transactional email service with a drag-and-drop template builder, delivery analytics, and Markdown-first authoring workflow.",
    category: "SaaS",
    demo: "https://example.com",
    techStack: ["Nuxt 3", "Resend", "PostgreSQL", "Drizzle ORM"],
    role: "Fullstack Engineer",
    year: "2023",
  },
  {
    slug: "terrafold",
    title: "Terrafold",
    shortDescription:
      "A CLI tool for declarative infrastructure teardown — generate cleanup plans from Terraform state and preview costs before you destroy.",
    category: "DevOps",
    github: "https://github.com",
    image:
      "https://images.unsplash.com/photo-1667372393119-3d4c48d07fc9?w=800&auto=format&fit=crop",
    techStack: ["Go", "Terraform", "Cobra CLI", "AWS SDK"],
    role: "Creator",
    year: "2022",
  },
  {
    slug: "inkframe",
    title: "Inkframe",
    shortDescription:
      "A minimalist writing environment with focus mode, spaced-repetition note linking, and seamless export to Notion, Obsidian, and PDF.",
    category: "Productivity",
    image:
      "https://images.unsplash.com/photo-1455390582262-044cdead277a?w=800&auto=format&fit=crop",
    demo: "https://example.com",
    techStack: ["Electron", "Vue 3", "SQLite", "Markdown-it"],
    role: "Product Engineer",
    year: "2022",
  },
   {
    slug: "inkframe",
    title: "Inkframe",
    shortDescription:
      "A minimalist writing environment with focus mode, spaced-repetition note linking, and seamless export to Notion, Obsidian, and PDF.",
    category: "Productivity",
    image:
      "https://images.unsplash.com/photo-1455390582262-044cdead277a?w=800&auto=format&fit=crop",
    demo: "https://example.com",
    techStack: ["Electron", "Vue 3", "SQLite", "Markdown-it"],
    role: "Product Engineer",
    year: "2022",
  },
];
</script>

<template>
  <section
    id="projects"
    className="relative  pt-32 pb-24 overflow-hidden"
  >
    <!-- <div className="absolute top-0 w-full transform -translate-y-1">
      <CurveDivider className="text-background" fill="fill-muted/10" />
    </div> -->

    <div
      className="container mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 relative z-10"
    >
      <div
        className="flex flex-col md:flex-row justify-between items-end mb-16 gap-6"
      >
        <div className="max-w-2xl">
          <div
            className="flex items-center gap-2 mb-4 text-primary font-medium"
          >
            <Sparkles className="w-5 h-5" />
            <span>Selected Works</span>
          </div>
          <h2 className="text-4xl md:text-5xl font-bold tracking-tight mb-4">
            From Concept <br />
            <span
              className="text-transparent bg-clip-text bg-gradient-to-r from-primary to-accent"
            >
              To Working Product
            </span>
          </h2>
          <p className="text-lg text-muted-foreground leading-relaxed">
            A curated selection of projects where ideas were translated into
            functional, user-focused applications.
          </p>
        </div>

        <div>
          <Button size="lg" variant="ghost" asChild className="group">
            <Link href="/projects">
              View Full Archive
              <ArrowRight
                className="ml-2 h-4 w-4 transition-transform group-hover:translate-x-1"
              />
            </Link>
          </Button>
        </div>
      </div>

      <div className="grid gap-10 sm:grid-cols-2 lg:grid-cols-3">
        <ProjectCard
          v-for="project in projects"
          :key="project.slug"
          :project="project"
        />
      </div>
    </div>
  </section>
</template>
