<script setup>
import FontText from "@/components/FontText.vue";
import peneImg from "/pene-img.png";
import Button from "@/components/Button.vue";
</script>

<template>
  <div class="flex flex-col justify-center items-center">
    <img
      class="h-22 rounded-full border-4 border-white shadow-md"
      :src="peneImg"
      alt=""
    />
    <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
      John Steven R. Penecitos.
    </FontText>
    <FontText addedClass="text-[#0e221b] text-center" sizeVariant="largebold">
      Experienced in fullstack development, using
      <span class="font-bold">Laravel</span> for developing website and web
      applications and a freelancer.
    </FontText>
    <div className="flex lg:gap-10 gap-5">
      <Button buttonVariant="primary" href="https://www.linkedin.com/in/john-steven-penecitos-38658a26a/" openInNewTab>Contact Me</Button>
      <Button buttonVariant="secondary" download="Penecitos_Resume.pdf">Download CV</Button>
    </div>
  </div>
</template>
