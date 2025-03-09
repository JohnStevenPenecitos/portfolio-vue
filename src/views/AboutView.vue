<template>
  <div class="flex flex-col justify-center items-center mt-14">
    <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
      About.
    </FontText>
    <FontText addedClass="text-[#0e221b] text-center" sizeVariant="largebold">
      Experienced in fullstack development, using Laravel for developing
      websites and web applications, and a freelancer.
    </FontText>

    <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
      Tools used.
    </FontText>
    <div class="grid grid-cols-2 md:grid-cols-4 gap-10 my-5">
      <SquareShadow
        v-for="(tool, index) in tools"
        :key="index"
        size="h-full w-28"
      >
        <Icons :icon="tool.icon" />
      </SquareShadow>
    </div>
  </div>
</template>

<script setup>
import FontText from "@/components/FontText.vue";
import SquareShadow from "@/components/SquareShadow.vue";
import Icons from "@/components/Icons.vue";

const tools = [
  { icon: "/icons/html-new.png" },
  { icon: "/icons/css-new.png" },
  { icon: "/icons/js.png" },
  { icon: "/icons/php.png" },
  { icon: "/icons/typescript.png" },
  { icon: "/icons/tail-wind.png" },
  { icon: "/icons/Laravel.png" },
  { icon: "/icons/mysql.avif" },
  { icon: "/icons/mongo.png" },
];
</script>
