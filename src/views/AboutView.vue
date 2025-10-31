<template>
  <div class="w-full flex flex-col items-center gap-56">
    <!-- HERO SECTION -->
    <section
      class="max-w-4xl mx-auto  flex md:flex-row flex-col justify-center items-center gap-5 mt-20"
    >
      <img
        class="w-72 rounded-4xl border-4 border-white shadow-md"
        :src="peneImg"
        alt=""
      />
      <div>
        <FontText addedClass="text-[#0e221b] my-4 text-center" sizeVariant="xlbold">
          About Me
        </FontText>
        <FontText addedClass="text-[#0e221b] my-4" sizeVariant="medium">
          I’m <span class="font-semibold">John Steven R. Penecitos</span>, a
          passionate
          <span class="font-semibold">Fullstack Developer and Freelancer</span>
          based in the Philippines. I specialize in building modern, scalable,
          and efficient web applications using
          <span class="text-[#0e221b] font-medium dark:text-white">Laravel</span
          >,
          <span class="text-[#0e221b] font-medium dark:text-white">Vue.js</span
          >, and
          <span class="text-[#0e221b] font-medium dark:text-white"
            >Tailwind CSS</span
          >. My goal is to turn ideas into digital solutions that are both
          functional and visually engaging. <br /><br />
          I’m currently focused on
          <span class="font-semibold">building full-stack systems</span> with a
          strong emphasis on
          <span class="font-semibold">backend development</span>, while also
          aspiring to grow my skills as a
          <span class="font-semibold">website designer</span>.
        </FontText>
      </div>
    </section>

    <section
      class="max-w-4xl flex flex-col justify-center items-center gap-5"
    >
        <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
          My Experiences
        </FontText>
      <div
        class="relative border-l-4 border-[#0e221b] dark:border-zinc-600 pl-6 space-y-10"
      >
        <div v-for="(exp, index) in experiences" :key="index" class="relative">
          <div
            class="absolute -left-3 top-3 w-3 h-3 bg-[#0e221b] dark:bg-white rounded-full"
          ></div>
          <div class="ml-4">
            <FontText addedClass="text-[#0e221b] my-4" sizeVariant="largebold">
              {{ exp.role }}</FontText
            >
            <FontText addedClass="text-[#0e221b] my-4" sizeVariant="mediumbold">
              {{ exp.year }}</FontText
            >
            <FontText addedClass="text-[#0e221b] my-4" sizeVariant="smallbold">
              {{ exp.company }}</FontText
            >
            <FontText addedClass="text-[#0e221b] my-4" sizeVariant="small">
              {{ exp.description }}</FontText
            >
          </div>
        </div>
      </div>
    </section>

   
    <section class="w-full mx-auto">
      <div class="max-w-4xl flex flex-col justify-center items-center">
        <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
          What I Do
        </FontText>
        <div class="grid md:grid-cols-2 gap-10 text-gray-700 text-lg">
          <div
            v-for="(item, index) in works"
            :key="index"
            class="bg-white dark:bg-zinc-900 shadow-[8px_8px_0px_rgba(0,0,0,1)] shadow-zinc-400 dark:shadow-zinc-800 rounded-2xl p-6 hover:shadow-lg transition flex flex-col items-center"
          >
            <Icons :icon="item.icon" />
            <FontText addedClass="text-[#0e221b] my-4" sizeVariant="mediumbold">
              {{ item.title }}</FontText
            >
            <FontText addedClass="text-[#0e221b]" sizeVariant="small">
              {{ item.description }}</FontText
            >
          </div>
        </div>
      </div>
    </section>

    <!-- TOOLS SECTION -->
    <section class="flex flex-col justify-center items-center mb-40 bg-amber-500">
      <div
        class="max-w-4xl mx-auto  flex flex-col justify-center items-center"
      >
        <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
          Tools & Tech Stack
        </FontText>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-10 my-5">
          <SquareShadow
            v-for="(tool, index) in tools"
            :key="index"
            size="h-full w-28"
            class="transition transform hover:scale-105"
          >
            <Icons :icon="tool.icon" />
          </SquareShadow>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from "vue";
import FontText from "@/components/FontText.vue";
import SquareShadow from "@/components/SquareShadow.vue";
import Icons from "@/components/Icons.vue";
import peneImg from "/stb.jpg";

const scrollToSection = (id) => {
  const section = document.getElementById(id);
  if (section) section.scrollIntoView({ behavior: "smooth" });
};

import toolsData from "@/data/tools.json";

const tools = ref(toolsData);

const experiences = [
  {
    year: "Aug 2024",
    role: "Freelance",
    company: "Department of Science and Technology – Taguig City",
    description:
      "Developed and maintained system components, participated in code reviews, and followed Agile methodology for software development.",
  },
  {
    year: "Apr 2023 – Aug 2023",
    role: "System Developer Intern",
    company: "Department of Science and Technology – Taguig City",
    description:
      "Developed and maintained system components, participated in code reviews, and followed Agile methodology for software development.",
  },
  {
    year: "Aug 2022 – Oct 2022",
    role: "Technical Support Intern",
    company: "ATOS Information Technology – Taguig City",
    description:
      "Assisted in diagnosing and resolving software and hardware issues while providing on-site user support.",
  },
  {
    year: "Nov 2019 – Jan 2020",
    role: "Data Encoder",
    company: "National Home Mortgage Finance Corporation – Makati City",
    description:
      "Entered and verified large volumes of data, ensuring accuracy and organization of records in Excel and company databases.",
  },
];

const works = [
  {
    title: "Full-Stack Web Development",
    icon: "/icons/8.png",
    description:
      "I build and maintain complete web systems from frontend to backend using Laravel and Vue.js. My focus now leans toward backend development—creating robust, scalable, and secure logic.",
  },
  {
    title: "API Integration & Automation",
    icon: "/icons/5.png",
    description:
      "I design and integrate RESTful APIs and build automation solutions that streamline workflows and connect applications seamlessly.",
  },
  {
    title: "Email & Visual Design",
   icon: "/icons/7.png",
    description:
      "I craft visually engaging email layouts and marketing assets, combining HTML email design and graphic design to deliver cohesive brand visuals.",
  },
  {
    title: "System Maintenance & Optimization",
    icon: "/icons/6.png",
    description:
      "I monitor, debug, and enhance system performance—improving stability, scalability, and efficiency for production-ready applications.",
  },
];

</script>

<style scoped>
html {
  scroll-behavior: smooth;
}
</style>
