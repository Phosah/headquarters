<script setup lang="ts">
defineEmits(["deleteTask"]);
const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
});
const taskCompleted = () => {
  props.todo.completed = !props.todo.completed;
};
</script>

<template>
  <section class="flex gap-3 mb-2 p-2 border border-gray-600 rounded-md">
    <input
      @change="taskCompleted()"
      type="checkbox"
      name="check-todo"
      id="check-todo"
    />
    <p :class="todo.completed ? 'line-through' : ''" class="flex-1">
      {{ todo.name }}
    </p>
    <button @click="$emit('deleteTask', todo.id)" class="text-red-700">
      &times;
    </button>
  </section>
</template>
