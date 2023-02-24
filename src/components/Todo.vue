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
  <div class="flex gap-3">
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
      X
    </button>
  </div>
</template>
