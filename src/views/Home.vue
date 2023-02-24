<script setup lang="ts">
import { ref, type Ref } from "vue";
import Todo from "@/components/Todo.vue";
const todoInput = ref("");
const todos: Ref<any> = ref([
  {
    id: 1,
    name: "Create todo app",
    completed: false,
  },
  {
    id: 2,
    name: "Implement Gruve changes",
    completed: false,
  },
]);
const addTodo = () => {
  todos.value.unshift({ name: todoInput.value, completed: false });
  console.log(todos.value);
  todoInput.value = "";
};
const deletedTask = (id: number) => {
  todos.value = todos.value.filter((todo: { id: number }) => todo.id !== id);
};
</script>

<template>
  <main class="flex flex-col items-center max-w-3xl mx-auto py-6 bg-red-100">
    <section>
      <p v-if="todos.length < 0" class="mb-4 text-sm">No todos currently</p>
      <form class="mb-4">
        <input
          v-model="todoInput"
          type="text"
          name="todos"
          id="todos"
          placeholder="Enter todo"
        />
        <button
          @click.prevent="addTodo()"
          class="w-12 ml-2 bg-red-500 rounded-md"
        >
          Add
        </button>
      </form>
      <div v-for="(todo, ix) in todos" :key="ix">
        <Todo :todo="todo" @delete-task="deletedTask(todo.id)" />
      </div>
    </section>
  </main>
</template>
