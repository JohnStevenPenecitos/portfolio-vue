<template>
  <transition name="fade">
    <div
      v-if="isOpen"
      class="fixed inset-0 z-50 flex items-center justify-center bg-black/60 backdrop-blur-sm transition-opacity"
      @click.self="close"
    >
      <div
        class="bg-white rounded-lg shadow-xl w-full max-w-3xl mx-2 md:mx-0 text-gray-800 transform transition-all duration-300 scale-100 flex flex-col items-center justify-center "
      >
        <div class="flex justify-between items-center border-b p-4 w-full">
          <h3 class="text-lg font-semibold text-blue-600">
            {{ title }}
          </h3>
          <button
            @click="close"
            class="text-gray-400 hover:text-gray-600 text-2xl leading-none"
          >
            <i class="fa-solid fa-xmark"></i>
          </button>
        </div>

        <div class="aspect-video bg-red-200 w-full flex flex-col">
          <iframe
            v-if="videoId"
            class="h-full w-full"
            :src="`https://www.youtube.com/embed/${extractVideoId(
              videoId
            )}?autoplay=1&rel=0`"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe>
          <div class="p-4">fsafsdfsfda</div>
        </div>

        <div class="flex flex-col border-b p-4 w-full">
          <div>Techstack:</div>
          <h3 class="text-lg font-semibold text-blue-600">
            {{ techStack }}
          </h3>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
const props = defineProps({
  isOpen: Boolean,
  title: String,
  videoId: String,
  techStack: Array,
});

const emits = defineEmits(["close"]);

const close = () => emits("close");

const extractVideoId = (url) => {
  if (!url) return "";
  const match = url.match(
    /(?:youtube\.com\/(?:.*v=|embed\/)|youtu\.be\/)([a-zA-Z0-9_-]{11})/
  );
  return match ? match[1] : url;
};
</script>
