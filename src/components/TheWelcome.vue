<template>
  <div class="flex flex-col justify-center items-center p-2 mt-14">
    <div class="text-center">
      <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
        Featured Projects.
      </FontText>
    </div>

    <!-- Projects Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10 my-5">
      <SquareShadow
        v-for="(project, index) in projects"
        :key="index"
        size="w-[50rem] h-full p-5"
        class="transition transform hover:scale-105 cursor-pointer"
        @click="openModal(project)"
      >
        <div>
          <div
            v-if="project.isBgImage"
            class="h-48 bg-cover bg-center flex items-center justify-center"
            :style="{ backgroundImage: `url('${project.image}')` }"
          ></div>
          <img
            v-else
            :src="project.image"
            class="w-full h-44 object-contain"
            alt=""
          />
          <FontText addedClass="text-[#0e221b] my-4" sizeVariant="largebold">
            {{ project.name }}
          </FontText>
          <FontText
            addedClass="text-[#0e221b] text-justify"
            sizeVariant="small"
          >
            {{ project.description }}
          </FontText>
        </div>
      </SquareShadow>
    </div>

    <Modal
      :isOpen="showModal"
      :title="selectedProject?.name"
      :videoId="selectedProject?.youtubeId"
      :techStack="selectedProject?.techStack"
      @close="showModal = false"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import FontText from "./FontText.vue";
import Modal from "./Modal.vue";
import SquareShadow from "./SquareShadow.vue";
import ecrsImg from "@/assets/system-ss/ECRS.png";
import smsImg from "@/assets/system-ss/SMS.png";
import ilypImg from "@/assets/system-ss/ILYP.png";
import ciebotImg from "@/assets/system-ss/CIEBOT.png";
import pokedexImg from "@/assets/system-ss/PokeDex.png";
import strkImg from "@/assets/system-ss/StreakCard.png";
import vrznImg from "@/assets/system-ss/Vrzn.png";

const showModal = ref(false);
const selectedProject = ref(null);

const openModal = (project) => {
  selectedProject.value = project;
  showModal.value = true;
};

const projects = [
  {
    name: "E-Class Record System",
    image: ecrsImg,
    description:
      "A digital platform for managing student grades and class records efficiently. It automates computation, ensuring accuracy and ease of use for educators.",
    isBgImage: true,
    youtubeId: "https://youtu.be/A1B2C3D4E5",
    techStack: ["Laravel", "MySQL", "Tailwind CSS", "jQuery"],
  },
  {
    name: "CIEBOT",
    image: ciebotImg,
    description:
      "An AI-powered chatbot that assists students with academic inquiries. It provides instant responses, helping users with common school-related concerns.",
    isBgImage: true,
    youtubeId: "https://youtu.be/F6G7H8I9J0",
    techStack: ["Vue.js", "OpenAI API", "Laravel", "Socket.io"],
  },
  {
    name: "ILetUPass",
    image: ilypImg,
    description:
      "A study aid designed to help students prepare for board exams. It offers quizzes, review materials, and performance tracking for effective learning.",
    isBgImage: true,
    youtubeId: "https://youtu.be/K1L2M3N4O5",
    techStack: ["Vue.js", "Firebase", "Tailwind CSS"],
  },
  {
    name: "Sanction Management System",
    image: smsImg,
    description:
      "A system designed to track and manage disciplinary actions in schools or organizations. It streamlines sanction logging and improves accountability.",
    isBgImage: true,
    youtubeId: "https://youtu.be/P6Q7R8S9T0",
    techStack: ["Laravel", "MySQL", "Bootstrap"],
  },
  {
    name: "Streak Card",
    image: strkImg,
    description:
      "A digital reward and loyalty tracking system that helps users maintain streaks for activities, encouraging consistency and engagement.",
    isBgImage: true,
    youtubeId: "https://youtu.be/U1V2W3X4Y5",
    techStack: ["Vue.js", "Tailwind CSS", "Supabase"],
  },
  {
    name: "Verizon Bank",
    image: vrznImg,
    description:
      "A modern banking platform offering secure transactions, intuitive financial management tools, and seamless online banking experiences.",
    isBgImage: true,
    youtubeId: "https://youtu.be/Z6A7B8C9D0",
    techStack: ["Laravel", "PostgreSQL", "Vue.js", "Inertia"],
  },
  {
    name: "PokeDex",
    image: pokedexImg,
    description:
      "A comprehensive database for Pokémon enthusiasts. It includes details on Pokémon stats, evolutions, and abilities, making it a perfect reference for trainers.",
    isBgImage: true,
    youtubeId: "https://youtu.be/E7F8G9H0I1",
    techStack: ["Vue.js", "PokeAPI", "Tailwind CSS"],
  },
];
</script>
