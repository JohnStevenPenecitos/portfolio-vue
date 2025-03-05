<template>
  <div class="flex flex-col justify-center items-center">
    <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
      About.
    </FontText>
    <FontText addedClass="text-[#0e221b] text-center" sizeVariant="largebold">
      Experienced in fullstack development, using Laravel for developing website
      and web applications and a freelancer.
    </FontText>

    <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
      Tools used.
    </FontText>
    <div class="grid grid-cols-1 md:grid-cols-4 gap-10 my-5">
      <SquareShadow size="h-full w-28"
        ><Icons icon="/icons/html.png"
      /></SquareShadow>
      <SquareShadow size="h-full w-28"
        ><Icons icon="/icons/css.svg"
      /></SquareShadow>
      <SquareShadow size="h-full w-28"
        ><Icons icon="/icons/tailwind.png" 
      /></SquareShadow>
      <SquareShadow size="h-full w-28"
        ><Icons icon="/icons/Laravel.png"
      /></SquareShadow>
      <SquareShadow size="h-full w-28"
        ><Icons icon="/icons/mysql.avif"
      /></SquareShadow>
      <SquareShadow size="h-full w-28"
        ><Icons icon="/icons/mongo.png"
      /></SquareShadow>
    </div>
  </div>
</template>

<script>
import FontText from "@/components/FontText.vue";
import SquareShadow from "@/components/SquareShadow.vue";
import Icons from "@/components/Icons.vue";

export default {
  components: {
    FontText,
    SquareShadow,
    Icons,
  },
};
</script>
