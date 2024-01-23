<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import { injectToast } from "nuxt-ui-vue";

injectToast();
</script>

<template>
  <div class="flex flex-col items-center justify-center">
    <HelloWorld msg="Vite + Vue" />
    <UNotifications position="top-right" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
