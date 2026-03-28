<template>
  <section id="contact" class="relative pt-32 pb-24 overflow-hidden">
    <!-- Background image collage -->
    <!-- <img
      src="/images/projects/collage-2.png"
      alt="Projects Collage"
      class="absolute inset-0 w-full h-full object-cover opacity-[0.20] dark:opacity-[0.10] pointer-events-none z-0 mix-blend-screen dark:mix-blend-lighten"
    /> -->

    <!-- Top Divider -->
    <!-- <div class="absolute top-0 w-full transform -translate-y-1 z-10">
      <CurveDivider class-name="text-muted/30" fill="fill-muted/30" />
    </div> -->

    <div class="container mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid lg:grid-cols-2 gap-16 items-center">

        <!-- Left Column: Content -->
        <div
          ref="contentRef"
          :class="[
            'transition-all duration-700',
            contentInView ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-8',
          ]"
        >
          <div class="flex items-center gap-2 mb-4 text-primary font-medium">
            <MessageSquareIcon class="w-5 h-5" />
            <span>Get in Touch</span>
          </div>

          <h2 class="text-4xl md:text-5xl font-bold tracking-tight mb-6">
            Let's Build Something <br />
            <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-accent">
              Amazing Together
            </span>
          </h2>

          <p class="text-lg text-muted-foreground leading-relaxed mb-8">
            Have a project in mind or just want to say hi? I'm always open to discussing new
            projects, creative ideas or opportunities to be part of your visions.
          </p>

          <div class="space-y-6">
            <div class="flex items-center gap-4">
              <div class="w-12 h-12 rounded-full bg-primary/10 flex items-center justify-center text-primary">
                <MailIcon class="w-6 h-6" />
              </div>
              <div>
                <h3 class="font-semibold text-foreground">Email Me</h3>
                <a
                  href="mailto:steven.penecitos123@gmail.com"
                  class="text-muted-foreground hover:text-primary transition-colors"
                >
                  steven.penecitos123@gmail.com
                </a>
              </div>
            </div>

            <div class="flex items-center gap-4">
              <div class="w-12 h-12 rounded-full bg-primary/10 flex items-center justify-center text-primary">
                <FacebookIcon class="w-6 h-6" />
              </div>
              <div>
                <h3 class="font-semibold text-foreground">Facebook</h3>
                <a
                  href="https://www.facebook.com/jspenecitos"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-muted-foreground hover:text-primary transition-colors"
                >
                  John Steven Penecitos
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- Right Column: Form -->
        <div
          ref="formRef"
          :class="[
            'bg-card/50 backdrop-blur-sm border border-border/50 rounded-2xl p-8 shadow-xl transition-all duration-700 delay-200',
            formInView ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-8',
          ]"
        >
          <form @submit.prevent="onSubmit" class="space-y-6" novalidate>

            <!-- Name -->
            <div class="space-y-2">
              <label class="text-sm font-medium text-foreground">Name</label>
              <input
                v-model="form.name"
                type="text"
                placeholder="Your Name"
                class="w-full rounded-md border border-primary/20 bg-background/50 px-3 py-2 text-sm placeholder:text-muted-foreground focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-colors"
                :class="{ 'border-destructive focus:border-destructive focus:ring-destructive': errors.name }"
              />
              <p v-if="errors.name" class="text-xs text-destructive">{{ errors.name }}</p>
            </div>

            <!-- Email -->
            <div class="space-y-2">
              <label class="text-sm font-medium text-foreground">Email</label>
              <input
                v-model="form.email"
                type="email"
                placeholder="your@email.com"
                class="w-full rounded-md border border-primary/20 bg-background/50 px-3 py-2 text-sm placeholder:text-muted-foreground focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-colors"
                :class="{ 'border-destructive focus:border-destructive focus:ring-destructive': errors.email }"
              />
              <p v-if="errors.email" class="text-xs text-destructive">{{ errors.email }}</p>
            </div>

            <!-- Facebook (Optional) -->
            <div class="space-y-2">
              <label class="text-sm font-medium text-foreground">Facebook <span class="text-muted-foreground">(Optional)</span></label>
              <input
                v-model="form.facebook"
                type="text"
                placeholder="Your Facebook Profile Link"
                class="w-full rounded-md border border-primary/20 bg-background/50 px-3 py-2 text-sm placeholder:text-muted-foreground focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-colors"
                :class="{ 'border-destructive focus:border-destructive focus:ring-destructive': errors.facebook }"
              />
              <p v-if="errors.facebook" class="text-xs text-destructive">{{ errors.facebook }}</p>
            </div>

            <!-- Message -->
            <div class="space-y-2">
              <label class="text-sm font-medium text-foreground">Message</label>
              <textarea
                v-model="form.message"
                placeholder="Tell me about your project..."
                rows="5"
                maxlength="2000"
                class="w-full rounded-md border border-primary/20 bg-background/50 px-3 py-2 text-sm placeholder:text-muted-foreground focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-colors resize-none"
                :class="{ 'border-destructive focus:border-destructive focus:ring-destructive': errors.message }"
              />
              <p v-if="errors.message" class="text-xs text-destructive">{{ errors.message }}</p>
            </div>

            <!-- Honeypot (hidden) -->
            <input
              v-model="form.honeypot"
              type="text"
              class="absolute left-[-9999px] opacity-0"
              tabindex="-1"
              autocomplete="off"
            />

            <!-- Submit -->
            <button
              type="submit"
              :disabled="isSubmitting"
              class="w-full inline-flex items-center justify-center gap-2 rounded-md bg-primary text-primary-foreground px-6 py-3 text-sm font-medium transition-colors hover:bg-primary/90 disabled:opacity-60 disabled:cursor-not-allowed"
            >
              <template v-if="isSubmitting">
                Sending...
                <Loader2Icon class="w-4 h-4 animate-spin" />
              </template>
              <template v-else>
                Send Message
                <SendIcon class="w-4 h-4" />
              </template>
            </button>

          </form>
        </div>

      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'
import {
  Send as SendIcon,
  Facebook as FacebookIcon,
  Mail as MailIcon,
  MessageSquare as MessageSquareIcon,
  Loader2 as Loader2Icon,
} from 'lucide-vue-next'
import { useIntersectionObserver } from '@vueuse/core'
import { toast } from 'vue-sonner'
import CurveDivider from '@/components/CurveDivider.vue'


const contentRef = ref<HTMLElement | null>(null)
const formRef = ref<HTMLElement | null>(null)
const contentInView = ref(false)
const formInView = ref(false)

useIntersectionObserver(contentRef, ([entry]) => {
  if (entry.isIntersecting) contentInView.value = true
}, { threshold: 0.2 })

useIntersectionObserver(formRef, ([entry]) => {
  if (entry.isIntersecting) formInView.value = true
}, { threshold: 0.2 })

const form = reactive({
  name: '',
  email: '',
  facebook: '',
  message: '',
  honeypot: '',
})

const errors = reactive({
  name: '',
  email: '',
  facebook: '',
  message: '',
})

const isSubmitting = ref(false)

function validate(): boolean {
  errors.name = ''
  errors.email = ''
  errors.facebook = ''
  errors.message = ''

  let valid = true

  if (form.name.length < 2) {
    errors.name = 'Name must be at least 2 characters.'
    valid = false
  } else if (form.name.length > 100) {
    errors.name = 'Name should not exceed 100 characters.'
    valid = false
  }

  if (!form.email) {
    errors.email = 'Email is required.'
    valid = false
  } else if (!/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(form.email)) {
    errors.email = 'Please enter a valid email address.'
    valid = false
  }

  if (form.facebook) {
    if (form.facebook.length > 300) {
      errors.facebook = 'Facebook link too long.'
      valid = false
    } else if (!/^(https?:\/\/)?(www\.)?(facebook\.com|fb\.com|m\.facebook\.com)\/.+$/.test(form.facebook)) {
      errors.facebook = 'Please enter a valid Facebook profile URL.'
      valid = false
    }
  }

  if (form.message.length < 3) {
    errors.message = 'Message must be at least 3 characters.'
    valid = false
  } else if (form.message.length > 2000) {
    errors.message = 'Message should not exceed 2,000 characters.'
    valid = false
  }

  return valid
}

async function onSubmit() {
  if (!validate()) return

  isSubmitting.value = true

  try {
    const response = await fetch('/api/contact', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ ...form }),
    })

    if (!response.ok) {
      const errorData = await response.json().catch(() => null)
      throw new Error(errorData?.error || 'Something went wrong')
    }

    Object.assign(form, { name: '', email: '', facebook: '', message: '', honeypot: '' })

    toast.success('Message sent successfully!', {
      description: "I'll get back to you as soon as possible.",
    })
  } catch (error) {
    toast.error('Failed to send message', {
      description: error instanceof Error ? error.message : 'Please try again later.',
    })
  } finally {
    isSubmitting.value = false
  }
}
</script>