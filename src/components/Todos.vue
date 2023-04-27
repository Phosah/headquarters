<script setup lang="ts">
import type { PropType } from "vue";
import Todo from "./Todo.vue";
defineEmits(["delete-task"]);
defineProps({
  allTodos: {
    type: Array as PropType<any[]>,
    required: true,
  },
});
</script>

<template>
  <section
    class="h-96 overflow-auto p-4 border border-gray-700 rounded-md space-y-2"
  >
    <div v-for="(todo, ix) in allTodos" :key="ix">
      <Todo :todo="todo" @delete-task="$emit('delete-task', todo.id)" />
    </div>
  </section>
</template>
