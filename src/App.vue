<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <nav class="flex justify-center gap-4 max-w-xl mx-auto py-6">
      <RouterLink to="/">Todos</RouterLink>
      <RouterLink to="/about">Review</RouterLink>
    </nav>
  </header>

  <RouterView />
</template>
