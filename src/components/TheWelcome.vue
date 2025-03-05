<template>
  <div class="flex flex-col justify-center items-center">
    <div class="text-center">
      <FontText addedClass="text-[#0e221b] my-4" sizeVariant="xlbold">
        Featured Projects.
      </FontText>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-4 gap-10 my-5">
      <SquareShadow size=" w-[50rem] h-full p-5">
        <div>
          <div class="bg-red-200 w-full h-44">fasdf</div>
          <FontText addedClass="text-[#0e221b] my-4" sizeVariant="largebold">
            Sanction Management System
          </FontText>
          <FontText addedClass="text-[#0e221b]" sizeVariant="small">
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley ofasdf
            dasf asdf sdf
          </FontText>
        </div>
      </SquareShadow>
      <SquareShadow size=" w-[50rem] h-full p-5">
        <div>
          <div class="bg-red-200 w-full h-44">fasdf</div>
          <FontText addedClass="text-[#0e221b] my-4" sizeVariant="largebold">
            E-Class Record System
          </FontText>
          <FontText addedClass="text-[#0e221b]" sizeVariant="small">
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley ofasdf
            dasf asdf sdf
          </FontText>
        </div>
      </SquareShadow>
      <SquareShadow size=" w-[50rem] h-full p-5">
        <div>
          <div class="bg-red-200 w-full h-44">fasdf</div>
          <FontText addedClass="text-[#0e221b] my-4" sizeVariant="largebold">
            CIEBOT 
          </FontText>
          <FontText addedClass="text-[#0e221b]" sizeVariant="small">
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley ofasdf
            dasf asdf sdf
          </FontText>
        </div>
      </SquareShadow>
      <SquareShadow size=" w-[50rem] h-full p-5">
        <div>
          <div class="bg-red-200 w-full h-44">fasdf</div>
          <FontText addedClass="text-[#0e221b] my-4" sizeVariant="largebold">
            ILetUPass
          </FontText>
          <FontText addedClass="text-[#0e221b]" sizeVariant="small">
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley ofasdf
            dasf asdf sdf
          </FontText>
        </div>
      </SquareShadow>
      
    </div>
  </div>
</template>

<script>
import FontText from "./FontText.vue";
import SquareShadow from "./SquareShadow.vue";

export default {
  components: {
    FontText,
    SquareShadow,
  },
};
</script>
