<script setup>
import peneImg from "/stv-img.jpg";
import TypewriterEffect from "@/components/TypewriterEffect.vue";
import WaveDivider from "@/components/WaveDivider.vue";
import { ArrowRight, Sparkles } from "lucide-vue-next";
import { RouterLink } from "vue-router";
import Services from "./Services.vue";
import Project from "./Project.vue";
import Certificates from "./Certificates.vue";
import Contact from "./Contact.vue";
</script>

<template>
  <div class="flex flex-col">
    <section
      class="relative min-h-[90vh] overflow-hidden flex flex-col justify-center"
    >
      <!-- Background Atmosphere -->
      <!-- <HeroBackground /> -->

      <div
        className="container  relative z-10 px-4 mx-auto sm:px-6 lg:px-8 pt-20 lg:pt-0"
      >
        <div
          className="flex flex-col lg:flex-row items-center gap-12 lg:gap-20"
        >
          <!-- Visual Scene (Right on desktop / Top on mobile) -->
          <div
            class="order-last w-full lg:w-1/2 relative min-h-[300px] lg:min-h-[500px] lg:flex hidden items-center justify-center"
          >
            <div
              class="relative z-10 w-full max-w-sm lg:aspect-square bg-gradient-to-tr from-primary/10 to-transparent rounded-3xl lg:rounded-full border border-primary/20 backdrop-blur-sm flex flex-col lg:items-center lg:justify-center p-6 lg:p-0 gap-8 lg:gap-0"
            >
              <!-- Desktop Image -->
              <div
                class="hidden lg:block relative z-10 w-48 h-48 sm:w-64 sm:h-64 md:w-80 md:h-80 mx-auto p-5"
              >
                <div
                  class="w-full h-full rounded-full overflow-hidden border-4 border-background/20 shadow-2xl relative"
                >
                  <img
                    :src="peneImg"
                    alt="John Steven Penecitos"
                    class="object-cover"
                  />
                </div>
              </div>
            </div>
          </div>

          <!-- Content (Left on desktop / Bottom on mobile) -->
          <div class="w-full space-y-8 text-center lg:text-left">
            <div class="flex flex-col items-center lg:items-start lg:w-[32rem]">
              <!-- Badge -->
              <div
                class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-primary/10 border border-primary/20 text-primary text-sm font-medium"
              >
                <Sparkles class="w-4 h-4" />
                <span>Available for new opportunities</span>
              </div>

              <!-- Mobile & Tablet Avatar -->
              <div
                class="lg:hidden relative z-10 w-48 h-48 sm:w-64 sm:h-64 md:w-72 md:h-72 mx-auto mt-6 p-2 rounded-3xl bg-gradient-to-tr from-primary/20 to-transparent border border-primary/20 shadow-xl"
              >
                <div class="w-full h-full rounded-2xl overflow-hidden relative">
                  <img
                    :src="peneImg"
                    alt="John Steven Penecitos"
                    class="object-cover w-full h-full"
                  />
                </div>
              </div>
            </div>

            <!-- Heading -->
            <h1
              class="text-4xl lg:text-6xl font-bold tracking-tight leading-[1.1]"
            >
              Hi, I'm <br />
              <span
                class="text-transparent bg-clip-text bg-gradient-to-r from-primary via-accent to-primary"
              >
                <TypewriterEffect
                  :words="[
                    'John Steven Penecitos',
                    'a Web Developer',
                    'a Freelancer',
                  ]"
                  class="text-4xl lg:text-6xl font-bold tracking-tight leading-[1.1]"
                />
              </span>
            </h1>

            <!-- Description -->
            <p
              class="text-md text-muted-foreground leading-relaxed max-w-lg mx-auto lg:mx-0"
            >
              Transforming complex ideas into well-built web applications.
              Focused on quality, growth, and continuous improvement.
            </p>

            <!-- CTA Buttons -->
            <div
              class="flex flex-col sm:flex-row items-center gap-6 justify-center lg:justify-start"
            >
              <RouterLink
                to="#projects"
                class="inline-flex items-center rounded-full px-8 h-12 text-base bg-primary text-primary-foreground shadow-lg shadow-primary/25 hover:shadow-primary/40 transition-shadow font-medium"
                @click="
                  trackEvent('button_click', {
                    button_name: 'project_cta',
                    source: 'hero_section',
                  })
                "
              >
                View Projects
                <ArrowRight class="ml-2 h-4 w-4" />
              </RouterLink>

              <RouterLink
                to="#contact"
                class="inline-flex items-center rounded-full px-8 h-12 text-base hover:bg-primary/5 transition-colors font-medium"
                @click="
                  trackEvent('button_click', {
                    button_name: 'contact_cta',
                    source: 'hero_section',
                  })
                "
              >
                Initiate Contact
              </RouterLink>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom Wave Divider -->
      <!-- <div class="absolute bottom-0 w-full transform translate-y-1">
        <WaveDivider class="text-background" fill="fill-muted/30" />
      </div> -->
    </section>

    <Services />

    <Project />

    <Certificates />

    <!-- <Certificates /> -->

    <Contact />

  </div>
</template>
