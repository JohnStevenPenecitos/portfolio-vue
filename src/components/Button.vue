<template>
  <div :class="computedClasses">
    <p><slot></slot></p>
  </div>
</template>

<script setup>
import { computed, defineProps } from "vue";

const props = defineProps({
  buttonVariant: {
    type: String,
    required: true,
    validator: (value) => ["primary" | "secondary"].includes(value),
  },
  addedClass: {
    type: String,
    default: "",
  },
});

const buttonVariants = {
  primary: "cursor-pointer rounded-full w-42  p-3 bg-[#0e221b] font-bold text-center my-7 text-white",
  secondary:
    "rounded-full w-42  p-3 bg-white text-[#0e221b] font-bold text-center my-7 cursor-pointer",
};

const computedClasses = computed(() => {
  return `${buttonVariants[props.buttonVariant]} ${props.addedClass}`.trim();
});
</script>
