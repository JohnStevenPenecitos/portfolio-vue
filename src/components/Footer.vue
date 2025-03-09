<template>
  <div
    v-motion
    :initial="{
      opacity: 0,
      y: 100,
    }"
    :enter="{
      opacity: 1,
      y: 0,
    }"
    class="justify-center items-center p-3 flex rounded-box"
  >
    <h1 class="font-bold">© 2025 Zern Codes. All rights reserved.</h1>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
