<template>
  <div :class="cn('flex flex-col space-y-1.5 p-6', class_)" v-bind="$attrs">
    <slot />
  </div>
</template>

<script setup lang="ts">
import { cn } from '@/lib/utils'

defineOptions({ inheritAttrs: false })

const props = defineProps<{
  class?: string
}>()

const class_ = props.class
</script>