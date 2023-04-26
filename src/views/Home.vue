<script setup lang="ts">
import { ref, type Ref } from "vue";
import Todos from "@/components/Todos.vue";
const todoInput = ref("");
// const todos: Ref<any> = ref([
//   {
//     id: 1,
//     name: "Create todo app",
//     completed: false,
//   }
// ]);

const todos = ref<any[]>(
  JSON.parse((localStorage.getItem("todos") as string) ?? "[]")
);

console.log(todos);

const addTodo = () => {
  const newTodo = {
    id: todos.value.length + 1,
    name: todoInput.value,
    completed: false,
  };

  todos.value = [newTodo, ...todos.value];

  // Add to local storage
  localStorage.setItem("todos", JSON.stringify(todos.value));
  console.log(todos.value);

  // Clear input
  todoInput.value = "";
};
const deletedTask = (id: number) => {
  if (confirm("Are you sure ?")) {
    todos.value = todos.value.filter((todo: { id: number }) => todo.id !== id);

    localStorage.setItem("todos", JSON.stringify(todos.value));
  }
};
</script>

<template>
  <main class="flex flex-col items-center max-w-3xl mx-auto py-6">
    <section>
      <p v-if="todos.length < 0" class="mb-4 text-sm">No todos currently</p>
      <form class="mb-4">
        <input
          class="p-2 rounded-md"
          v-model="todoInput"
          type="text"
          name="todos"
          id="todos"
          placeholder="Enter todo"
        />
        <button
          @click.prevent="addTodo()"
          class="w-12 ml-2 p-2 bg-red-500 rounded-md text-white"
        >
          Add
        </button>
      </form>
      <Todos :all-todos="todos" @delete-task="deletedTask" />
    </section>
  </main>
</template>
