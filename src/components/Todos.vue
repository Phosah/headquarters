<script setup lang="ts">
import Todo from "./Todo.vue";
defineEmits(["delete-task"]);
defineProps({
  allTodos: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <section class="p-4 border border-gray-700 rounded-md">
    <div v-for="(todo, ix) in allTodos" :key="ix">
      <Todo :todo="todo" @delete-task="$emit('delete-task', todo.id)" />
    </div>
  </section>
</template>
