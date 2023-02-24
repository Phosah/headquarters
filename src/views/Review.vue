<script setup lang="ts">
import { ref } from "vue";

const active = ref();
const activeColor = "bg-red-200";
const submitted = (i: number) => {
  active.value = i;
};
</script>

<template>
  <div class="Reviews">
    <h1>This is a review page</h1>
    <p>No reviews yet</p>
    <div class="border p-4">
      <div class="mb-2" v-for="(button, i) in 3" :key="i">
        <button
          @click="submitted(i)"
          :class="active == i ? activeColor : ''"
          class="border border-teal-700 px-3"
        >
          Text {{ i + 1 }}
        </button>
      </div>
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
