<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 flex justify-center transition-all duration-300',
      scrolled ? 'py-4' : 'py-6',
    ]"
  >
    <nav
      :class="[
        'relative flex items-center justify-between px-6 transition-all duration-300',
        scrolled
          ? 'w-[95%] max-w-5xl h-14 rounded-full bg-background/80 backdrop-blur-md border border-border shadow-lg supports-[backdrop-filter]:bg-background/60'
          : 'w-full max-w-7xl h-16 bg-transparent',
      ]"
    >
      <!-- Logo -->
      <button
        type="button"
        @click="scrollTo('/')"
        class="flex items-center space-x-2 group bg-transparent border-none outline-none"
      >
        <div class="p-1.5 rounded-lg bg-primary/10 group-hover:bg-primary/20 transition-colors">
          <Rocket class="w-5 h-5 text-primary" />
        </div>
        <span class="text-xl font-bold tracking-tight">JSP</span>
      </button>

      <!-- Desktop Navigation -->
      <div class="hidden lg:flex md:items-center md:space-x-8">
        <button
          v-for="link in links"
          :key="link.id"
          type="button"
          :class="[
            'p-2 rounded-full transition-all duration-200 cursor-pointer bg-transparent border-none',
            'dark:hover:bg-gray-800 hover:bg-gray-200',
          ]"
          @click="scrollTo(link.id)"
        >
          {{ link.name }}
        </button>
      </div>

      <!-- CTA Button (Desktop) -->
      <div class="hidden lg:flex items-center gap-4">
        <button
          type="button"
          :class="[
            'rounded-full shadow-md shadow-primary/20 bg-primary text-primary-foreground font-medium px-4 py-2 cursor-pointer border-none',
            scrolled ? 'text-sm' : 'text-base',
          ]"
          @click="scrollTo('contact')"
        >
          Let's Talk
        </button>
      </div>

      <!-- Mobile Menu Button -->
      <div class="flex items-center gap-2 lg:hidden">
        <button
          type="button"
          class="h-8 w-8 flex items-center justify-center rounded-md hover:bg-accent transition-colors"
          @click="mobileMenuOpen = !mobileMenuOpen"
          aria-label="Toggle menu"
        >
          <X v-if="mobileMenuOpen" class="h-5 w-5" />
          <Menu v-else class="h-5 w-5" />
        </button>
      </div>

      <!-- Mobile Menu Dropdown -->
      <div
        :class="[
          'absolute top-full left-0 right-0 mt-4 p-4 mx-4 rounded-2xl',
          'bg-background/95 backdrop-blur-xl border border-border shadow-xl',
          'lg:hidden flex flex-col space-y-4 transition-all duration-300 origin-top transform',
          mobileMenuOpen
            ? 'opacity-100 scale-100 translate-y-0 pointer-events-auto'
            : 'opacity-0 scale-95 -translate-y-4 pointer-events-none',
        ]"
      >
        <button
          v-for="link in links"
          :key="link.id"
          type="button"
          class="block w-full text-left px-4 py-3 rounded-xl text-base font-medium text-foreground/80 hover:bg-primary/10 hover:text-primary transition-colors cursor-pointer bg-transparent border-none"
          @click="scrollTo(link.id)"
        >
          {{ link.name }}
        </button>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { Rocket, Menu, X } from "lucide-vue-next";

const scrolled = ref(false);
const mobileMenuOpen = ref(false);

const links = [
  { name: "Home",      id: "/"        },
  { name: "Skills",    id: "services" },
  { name: "Portfolio", id: "projects" },
  { name: "Contact",   id: "contact"  },
];

const scrollTo = (id) => {
  if (id === "/") {
    window.scrollTo({ top: 0, behavior: "smooth" });
  } else {
    const el = document.getElementById(id);
    if (el) el.scrollIntoView({ behavior: "smooth" });
  }
  mobileMenuOpen.value = false;
};

const handleScroll = () => {
  scrolled.value = window.scrollY > 20;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));
</script>