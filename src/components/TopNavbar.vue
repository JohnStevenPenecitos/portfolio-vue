<template>
    <div class="flex justify-center items-center  absolute">
      <nav
        class="flex gap-8 justify-center items-center dark:bg-[#0e221b] bg-white  dark:text-white p-2 rounded-full shadow-md"
      >
        <RouterLink
          to="/"
          class="dark:hover:bg-gray-800 hover:bg-gray-200 p-2 rounded-full"
          :class="{ 'font-bold': $route.path === '/' }"
        >
          Home
        </RouterLink>
        <RouterLink
          to="/about"
          class="dark:hover:bg-gray-800 hover:bg-gray-200 p-2 rounded-full"
          :class="{ 'font-bold': $route.path === '/about' }"
        >
          About
        </RouterLink>
        <RouterLink
          to="/portfolio"
          class="dark:hover:bg-gray-800 hover:bg-gray-200 p-2 rounded-full"
          :class="{ 'font-bold': $route.path === '/portfolio' }"
        >
          Portfolio
        </RouterLink>
      </nav>
    </div>
</template>
