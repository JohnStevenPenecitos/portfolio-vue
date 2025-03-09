<template>
  <div class="flex flex-col justify-center items-center p-2 mt-14">
    <div class="text-center">
      <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
        Featured Projects.
      </FontText>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10 my-5">
      <SquareShadow
        v-for="(project, index) in projects"
        :key="index"
        size="w-[50rem] h-full p-5"
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
          <FontText addedClass="text-[#0e221b] text-justify" sizeVariant="small">
            {{ project.description }}
          </FontText>
        </div>
      </SquareShadow>
    </div>
  </div>
</template>

<script setup>
import FontText from "./FontText.vue";
import SquareShadow from "./SquareShadow.vue";
import ecrsImg from "@/assets/system-ss/ECRS.png";
import smsImg from "@/assets/system-ss/SMS.png";
import ilypImg from "@/assets/system-ss/ILYP.png";
import ciebotImg from "@/assets/system-ss/CIEBOT.png";
import pokedexImg from "@/assets/system-ss/PokeDex.png";

const projects = [
  {
    name: "E-Class Record System",
    image: ecrsImg,
    description:
      " A digital platform for managing student grades and class records efficiently. It automates computation, ensuring accuracy and ease of use for educators.",
    isBgImage: true,
  },

  {
    name: "CIEBOT",
    image: ciebotImg,
    description: "An AI-powered chatbot that assists students with academic inquiries. It provides instant responses, helping users with common school-related concerns.",
    isBgImage: true,
  },
  {
    name: "ILetUPass",
    image: ilypImg,
    description: "A study aid designed to help students prepare for board exams. It offers quizzes, review materials, and performance tracking for effective learning.",
    isBgImage: true,
  },
  {
    name: "PokeDex",
    image: pokedexImg,
    description: "A comprehensive database for Pokémon enthusiasts. It includes details on Pokémon stats, evolutions, and abilities, making it a perfect reference for trainers.",
    isBgImage: true,
  },
  {
    name: "Sanction Management System",
    image: smsImg,
    description: "A system designed to track and manage disciplinary actions in schools or organizations. It streamlines sanction logging and improves accountability.",
    isBgImage: true,
  },
  {
    name: "Streak Card",
    image: smsImg,
    description: "A system designed to track and manage disciplinary actions in schools or organizations. It streamlines sanction logging and improves accountability.",
    isBgImage: true,
  },
  {
    name: "Verizon Bank",
    image: smsImg,
    description: "A system designed to track and manage disciplinary actions in schools or organizations. It streamlines sanction logging and improves accountability.",
    isBgImage: true,
  },
];
</script>
