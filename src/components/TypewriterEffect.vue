<template>
  <span :class="className">
    {{ currentText }}
    <span
      :class="['inline-block ml-1 w-[2px] h-[1em] bg-primary align-middle animate-blink', cursorClassName]"
    />
  </span>
</template>

<script setup>
import { ref, watch, onUnmounted } from "vue";

const props = defineProps({
  words: {
    type: Array,
    required: true,
  },
  className: {
    type: String,
    default: "",
  },
  cursorClassName: {
    type: String,
    default: "",
  },
});

const currentWordIndex = ref(0);
const currentText = ref("");
const isDeleting = ref(false);

let timeout = null;

const tick = () => {
  const word = props.words[currentWordIndex.value];

  if (!isDeleting.value) {
    // Typing
    currentText.value = word.substring(0, currentText.value.length + 1);

    if (currentText.value.length === word.length) {
      // Pause before deleting
      timeout = setTimeout(() => {
        isDeleting.value = true;
        tick();
      }, 1500);
      return;
    }
  } else {
    // Deleting
    currentText.value = word.substring(0, currentText.value.length - 1);

    if (currentText.value.length === 0) {
      isDeleting.value = false;
      currentWordIndex.value = (currentWordIndex.value + 1) % props.words.length;
    }
  }

  timeout = setTimeout(tick, isDeleting.value ? 50 : 100);
};

// Start on mount
timeout = setTimeout(tick, 100);

onUnmounted(() => clearTimeout(timeout));
</script>

<style scoped>
@keyframes blink {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0; }
}

.animate-blink {
  animation: blink 0.8s linear infinite;
}
</style>