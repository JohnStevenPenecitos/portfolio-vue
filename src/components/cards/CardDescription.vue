<template>
  <div :class="cn('text-sm text-muted-foreground', class_)" v-bind="$attrs">
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