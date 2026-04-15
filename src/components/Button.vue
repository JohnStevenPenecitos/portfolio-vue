<!-- <template>
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
</script> -->


<template>
  <component
    :is="as"
    v-bind="$attrs"
    :class="cn(buttonVariants({ variant, size }), $attrs.class)"
    :disabled="disabled"
  >
    <slot />
  </component>
</template>

<script setup>
import { computed } from "vue";
import { cva } from "class-variance-authority";
import { cn } from "@/lib/utils";

defineOptions({ inheritAttrs: false });

const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium transition-colors focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg]:size-4 [&_svg]:shrink-0",
  {
    variants: {
      variant: {
        default:     "bg-primary text-primary-foreground shadow hover:bg-primary/90",
        destructive: "bg-destructive text-destructive-foreground shadow-sm hover:bg-destructive/90",
        outline:     "border border-input bg-background shadow-sm hover:bg-accent hover:text-accent-foreground",
        secondary:   "bg-secondary text-secondary-foreground shadow-sm hover:bg-secondary/80",
        ghost:       "hover:bg-accent hover:text-accent-foreground",
        link:        "text-primary underline-offset-4 hover:underline",
      },
      size: {
        default: "h-9 px-4 py-2",
        sm:      "h-8 rounded-md px-3 text-xs",
        lg:      "h-10 rounded-md px-8",
        icon:    "h-9 w-9",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
);

const props = defineProps({
  variant: {
    type: String,
    default: "default",
  },
  size: {
    type: String,
    default: "default",
  },
  as: {
    type: [String, Object],
    default: "button",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});

</script>