<template>
  <section id="certificates" class="  py-20 w-full">
    <div class="container mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mb-12 text-center">
        <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">
          Certificates & Achievements
        </h2>
        <p class="mt-4 text-lg text-muted-foreground">
          Professional certifications and completed courses
        </p>
      </div>

      <div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
        <div v-for="certificate in sortedCertificates" :key="certificate.id">
          <CertificateCard :certificate="certificate" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import CertificateCard, { Certificate } from '@/components/cards/CertificateCard.vue';
import { computed } from 'vue'

import udemyLogo from "@/assets/logo/udemy-logo.png";
import certLara from "@/assets/certs/cert-laravel.jpg";
import certn8n from "@/assets/certs/cert-n8n.jpg";


const certificates: Certificate[] = [
  {
    id: '1',
    title: 'AI Agent Automation using n8n',
    category: 'Automation',
    image: certn8n,
    href: 'https://www.udemy.com/certificate/UC-818558bb-48ed-4549-8f16-8ebc617907c0/',
    dateIssued: '2026',
    issuer: {
      name: 'Udemy',
    },
  },
  {
    id: '2',
    title: 'REST API Development',
    category: 'REST API',
    image: certLara,
    href: 'https://www.udemy.com/certificate/UC-267b8d85-d05f-4258-a398-271579f255d1/',
    dateIssued: '2025',
    issuer: {
      name: 'Udemy',
    },
  },
]

const sortedCertificates = computed(() =>
  [...certificates].sort(
    (a, b) => new Date(b.dateIssued).getTime() - new Date(a.dateIssued).getTime()
  )
)
</script>