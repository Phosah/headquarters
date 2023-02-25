<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <nav class="flex justify-center gap-4 max-w-xl px-6 mx-auto py-6">
      <RouterLink to="/">Todos</RouterLink>
      <RouterLink to="/about">Review</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>

<style>
.router-link-active {
  color: rgb(239 68 68);
  font-weight: 700;
}
</style>
