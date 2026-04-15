<template>
  <section id="services" class="py-24 overflow-hidden">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="text-center mb-16">
        <h2 class="text-3xl md:text-5xl font-bold tracking-tight mb-4">
          Crafting Digital <br />
          <span
            class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-accent"
          >
            Experiences
          </span>
        </h2>
        <p class="text-lg text-muted-foreground max-w-2xl mx-auto">
          From concept to deployment, I handle the entire lifecycle of modern
          web development.
        </p>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 mb-20">
        <ServicesCard
          v-for="(service, index) in services"
          :key="index"
          :service="service"
        />
      </div>
    </div>

    <div class="">
      <SkillsMarquee :skills="skills" :pause-on-hover="true" />
    </div>
  </section>
</template>

<script setup>
import ServicesCard from "@/components/cards/ServicesCard.vue";
import SkillsMarquee from "@/components/SkillsMarquee.vue";
import { Layout, Smartphone, Server, Bot } from "lucide-vue-next";
import { ref } from "vue";

defineProps({
  skills: {
    type: Array,
    required: true,
  },
});

const services = [
  {
    title: "Frontend Development",
    description:
      "Building responsive, pixel-perfect web interfaces using Vue.js as my primary framework, with working knowledge of React for component-based UI development.",
    icon: Layout,
    color: "text-blue-500",
  },
  {
    title: "Backend Development",
    description:
      "Building robust server-side applications and RESTful APIs primarily with PHP and Laravel, including thorough API testing to ensure reliability and performance.",
    icon: Server,
    color: "text-green-500",
  },
  {
    title: "Automation",
    description:
      "Building automated workflows and integrations that connect systems, eliminate manual tasks, and keep your processes running smoothly in the background.",
    icon: Bot,
    color: "text-purple-500",
  },
];

const skills = ref([
  {
    name: "Vue.js",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg",
  },
  {
    name: "React",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg",
  },
  {
    name: "Node.js",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg",
  },
  {
    name: "Tailwind CSS",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-original.svg",
  },
  {
    name: "MongoDB",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg",
  },
  {
    name: "Git",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg",
  },
  {
    name: "Laravel",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-original.svg",
  },
  {
    name: "MySQL",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg",
  },
  {
    name: "Nginx",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nginx/nginx-original.svg",
  },
  {
    name: "Postman",
    stackIcon:
      "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postman/postman-original.svg",
  },
]);
</script>
