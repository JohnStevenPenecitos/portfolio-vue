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
      <RouterLink to="/" class="flex items-center space-x-2 group">
        <div
          class="p-1.5 rounded-lg bg-primary/10 group-hover:bg-primary/20 transition-colors"
        >
          <Rocket class="w-5 h-5 text-primary" />
        </div>
        <span class="text-xl font-bold tracking-tight">JSPDev</span>
      </RouterLink>

      <!-- Desktop Navigation -->
      <div class="hidden lg:flex md:items-center md:space-x-8">
        <RouterLink
          v-for="link in links"
          :key="link.path"
          :to="link.path"
          :class="[
            'p-2 rounded-full transition-all duration-200',
            'dark:hover:bg-gray-800 hover:bg-gray-200',
            isActive(link.path)
              ? 'font-semibold text-primary'
              : 'text-foreground/80',
          ]"
        >
          {{ link.name }}
        </RouterLink>
      </div>

      <!-- CTA Buttons & Theme Toggle (Desktop) -->
      <div class="hidden lg:flex items-center gap-4">
        <ThemeToggle />
        <RouterLink
          to="/minigames"
          :class="[
            'rounded-full shadow-md hover:scale-105 transition-transform',
            'bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500',
            'text-white font-bold px-4 py-2 flex items-center gap-2',
            scrolled ? 'text-sm' : 'text-base',
          ]"
          @click="
            trackEvent('navigation_click', {
              link_name: 'Arcade',
              link_path: '/minigames',
              source: 'navbar_desktop',
            })
          "
        >
          <Rocket class="w-4 h-4 animate-bounce" />
          Arcade
        </RouterLink>

        <RouterLink
          to="/contact"
          :class="[
            'rounded-full shadow-md shadow-primary/20 bg-primary text-primary-foreground font-medium px-4 py-2',
            scrolled ? 'text-sm' : 'text-base',
          ]"
        >
          Let's Talk
        </RouterLink>
      </div>

      <!-- Mobile Menu Button -->
      <div class="flex items-center gap-2 lg:hidden">
        <ThemeToggle />
        <button
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
        <RouterLink
          v-for="link in links"
          :key="link.path"
          :to="link.path"
          class="block px-4 py-3 rounded-xl text-base font-medium text-foreground/80 hover:bg-primary/10 hover:text-primary transition-colors"
          @click="
            () => {
              trackEvent('navigation_click', {
                link_name: link.name,
                link_path: link.path,
                source: 'navbar_mobile',
              });
              mobileMenuOpen = false;
            }
          "
        >
          {{ link.name }}
        </RouterLink>

        <div class="flex flex-col gap-3 pt-2">
          <RouterLink
            to="/minigames"
            class="w-full rounded-xl bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 text-white font-bold px-4 py-2 text-center hover:opacity-90 transition-opacity flex items-center justify-center gap-2"
            @click="
              () => {
                trackEvent('navigation_click', {
                  link_name: 'Arcade',
                  link_path: '/minigames',
                  source: 'navbar_mobile',
                });
                mobileMenuOpen = false;
              }
            "
          >
            <Rocket class="w-4 h-4" />
            Arcade Center
          </RouterLink>

        </div>
      </div>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { useRoute } from "vue-router";
import { Rocket, Menu, X } from "lucide-vue-next";

const route = useRoute();
const scrolled = ref(false);
const mobileMenuOpen = ref(false);

const links = [
  { name: "Home", path: "/" },
  { name: "About", path: "/about" },
  { name: "Portfolio", path: "/portfolio" },
  { name: "Contact", path: "/contact" },
];

const isActive = (path) => route.path === path;

const handleScroll = () => {
  scrolled.value = window.scrollY > 20;
};

const trackEvent = (event, props) => {
  console.log("Track:", event, props);
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));
</script>
