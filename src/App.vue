<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from '@components/HelloWorld.vue'
</script>

<template>
  <div class="flex items-center">
    <a
      href="https://vitejs.dev"
      target="_blank"
      class="hover:drop-shadow-[0_0_2em_#646cffaa]"
    >
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a
      href="https://vuejs.org/"
      target="_blank"
      class="hover:drop-shadow-[0_0_2em_#42b883aa]"
    >
      <img src="./assets/vue.svg" class="logo" alt="Vue logo" />
    </a>
  </div>

  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  @apply h-24 p-6;
  will-change: filter;
}
</style>
