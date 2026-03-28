<template>
  <section id="certificates" class="  py-20 w-full">
    <div class="container mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="mb-12 text-center">
        <h2 class="text-3xl font-bold tracking-tight sm:text-4xl">
          Certificates & Achievements
        </h2>
        <p class="mt-4 text-lg text-muted-foreground">
          Professional certifications and completed courses
        </p>
      </div>

      <!-- Certificates Grid -->
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

const certificates: Certificate[] = [
  {
    id: '1',
    title: 'AWS Certified Solutions Architect – Associate',
    category: 'Cloud',
    image: 'https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=800&auto=format&fit=crop',
    href: 'https://aws.amazon.com/certification/',
    dateIssued: '2024-03-15',
    issuer: {
      name: 'Amazon Web Services',
      image: 'https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg',
    },
  },
  {
    id: '2',
    title: 'Google Professional Cloud Developer',
    category: 'Cloud',
    image: 'https://images.unsplash.com/photo-1573804633927-bfcbcd909acd?w=800&auto=format&fit=crop',
    href: 'https://cloud.google.com/certification',
    dateIssued: '2024-01-20',
    issuer: {
      name: 'Google Cloud',
    },
  },
  {
    id: '3',
    title: 'Meta Front-End Developer Professional Certificate',
    category: 'Frontend',
    image: 'https://images.unsplash.com/photo-1547658719-da2b51169166?w=800&auto=format&fit=crop',
    href: 'https://www.coursera.org/professional-certificates/meta-front-end-developer',
    dateIssued: '2023-11-05',
    issuer: {
      name: 'Meta / Coursera',
    },
  },
  {
    id: '4',
    title: 'MongoDB Associate Developer',
    category: 'Database',
    image: 'https://images.unsplash.com/photo-1558494949-ef010cbdcc31?w=800&auto=format&fit=crop',
    href: 'https://university.mongodb.com/certification',
    dateIssued: '2023-08-30',
    issuer: {
      name: 'MongoDB University',
    },
  },
  {
    id: '5',
    title: 'GitHub Actions Certification',
    category: 'DevOps',
    image: 'https://images.unsplash.com/photo-1618401471353-b98afee0b2eb?w=800&auto=format&fit=crop',
    href: 'https://github.com/education',
    dateIssued: '2023-06-12',
    issuer: {
      name: 'GitHub',
    },
  },
  {
    id: '6',
    title: 'Vue.js 3 – The Complete Guide dsaf asf asdf ',
    category: 'Frontend',
    dateIssued: '2023-04-01',
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