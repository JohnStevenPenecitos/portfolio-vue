<template>
  <Card class="group h-full flex flex-col overflow-hidden transition-all hover:shadow-lg">
    <CardHeader class="p-0">
      <div class="relative aspect-[16/10] overflow-hidden bg-muted">
        <div class="flex h-full w-full items-center justify-center bg-gradient-to-br from-primary/20 to-primary/5">
          <img
            v-if="certificate.image"
            :src="certificate.image"
            :alt="certificate.title"
            class="absolute inset-0 h-full w-full"
            loading="lazy"
          />
          <p v-else class="text-center text-sm text-muted-foreground">
            Certificate<br />
            <span class="text-xs">{{ certificate.title }}</span>
          </p>
        </div>

        <div class="absolute right-4 top-4">
          <span class="inline-flex items-center rounded-full bg-secondary text-secondary-foreground px-2.5 py-0.5 text-xs font-medium">
            {{ certificate.category }}
          </span>
        </div>

        <div
          v-if="certificate.href"
          class="absolute left-4 top-4 opacity-0 transition-opacity group-hover:opacity-100"
        >
          <div class="rounded-full bg-background p-2 shadow-lg">
            <ExternalLinkIcon class="h-4 w-4" />
          </div>
        </div>
      </div>
    </CardHeader>

    <CardContent class="p-6 flex-grow flex flex-col">
      <div class="mb-3 flex items-center gap-3">
        <div class="h-10 w-10 rounded-full bg-muted flex items-center justify-center overflow-hidden shrink-0">
          <img
            v-if="certificate.issuer.image"
            :src="certificate.issuer.image"
            :alt="certificate.issuer.name"
            class="h-full w-full"
          />
          <span v-else class="text-xs font-bold text-primary">
            {{ certificate.issuer.name.substring(0, 2).toUpperCase() }}
          </span>
        </div>
        <span class="text-sm font-medium text-muted-foreground">{{ certificate.issuer.name }}</span>
      </div>

      <CardTitle class="mb-2 text-lg font-bold text-foreground group-hover:text-primary transition-colors line-clamp-2">
        {{ certificate.title }}
      </CardTitle>

      <div class="flex items-center gap-2 mt-auto pt-4 text-sm text-muted-foreground">
        <CalendarIcon class="h-4 w-4" />
        <span>{{ formattedDate }}</span>
      </div>
    </CardContent>
  </Card>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { ExternalLink as ExternalLinkIcon, Calendar as CalendarIcon } from 'lucide-vue-next'
import Card from './Card.vue'
import CardHeader from './CardHeader.vue'
import CardContent from './CardContent.vue'
import CardTitle from './CardTitle.vue'

export interface Certificate {
  id: string
  title: string
  category: string
  image?: string
  href?: string
  dateIssued: string
  issuer: {
    name: string
    image?: string
  }
}

const props = defineProps<{ certificate: Certificate }>()

const formattedDate = computed(() =>
  new Date(props.certificate.dateIssued).toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'long',
  })
)
</script>