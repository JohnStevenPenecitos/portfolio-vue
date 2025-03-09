<template>
  <a
  v-motion-roll-visible-left
    v-if="href"
    :href="href"
    :target="openInNewTab ? '_blank' : '_self'"
    :download="download ? getFileName(download) : null"
    :class="computedClasses"
  >
    <slot></slot>
  </a>
  <button v-motion-roll-visible-left v-else @click="handleDownload" :class="computedClasses">
    <slot></slot>
  </button>
</template>

<script setup>
import { computed, defineProps } from "vue";

const props = defineProps({
  buttonVariant: {
    type: String,
    required: true,
    validator: (value) => ["primary", "secondary"].includes(value),
  },
  addedClass: {
    type: String,
    default: "",
  },
  href: {
    type: String,
    default: null, 
  },
  openInNewTab: {
    type: Boolean,
    default: false, 
  },
  download: {
    type: String,
    default: null, 
  },
});

const buttonVariants = {
  primary:
    "cursor-pointer rounded-full w-42 p-3 bg-[#0e221b] font-bold text-center my-7 text-white hover:bg-gray-800",
  secondary:
    "rounded-full w-42 p-3 bg-white hover:bg-gray-100 text-[#0e221b] font-bold text-center my-7 cursor-pointer",
};

const computedClasses = computed(() => {
  return `${buttonVariants[props.buttonVariant]} ${props.addedClass}`.trim();
});

const getFileName = (path) => path.split("/").pop();

const handleDownload = () => {
  if (props.download) {
    const link = document.createElement("a");
    link.href = `/${props.download}`; 
    link.download = getFileName(props.download);
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  }
};
</script>
