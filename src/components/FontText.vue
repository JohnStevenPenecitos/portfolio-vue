<template>
  <div :class="computedClasses">
    <p><slot></slot></p>
  </div>
</template>

<script setup>
import { computed, defineProps } from "vue";

const props = defineProps({
  sizeVariant: {
    type: String,
    required: true,
    validator: (value) =>
      [
        "small",
        "smallbold",
        "medium",
        "large",
        "xl",
        "xlbold",
        "xxlbold",
        "largebold",
        "mediumbold",
        "mediumbolditalic",
      ].includes(value),
  },
  addedClass: {
    type: String,
    default: "",
  },
});

const sizeVariants = {
  small: "text-sm md:text-base",
  smallbold: "text-sm md:text-base font-bold my-3",
  medium: "text-base md:text-lg",
  large: "text-xl lg:text-2xl",
  xl: "text-3xl lg:text-4xl",
  largebold: "text-xl lg:text-2xl font-bold",
  mediumbold: "text-base md:text-lg font-bold",
  mediumbolditalic: "text-base md:text-md font-bold italic",
  xlbold: "text-3xl lg:text-4xl font-semibold",
  xxlbold: "text-5xl font-semibold",
};

const computedClasses = computed(() => {
  return `${sizeVariants[props.sizeVariant]} ${props.addedClass}`.trim();
});
</script>
