<template>
  <div class="flex flex-col items-center justify-center w-1/2 mx-auto">
    <div class="w-full flex flex-col px-8 py-4">
      <div class="w-full text-3xl py-4">Todo</div>

      <NewTodoBox :todos="todos" />

      <TodoList :todos="todos" />
    </div>
    <button
      class="bg-blue-500 px-4 rounded-md text-white"
      @click="() => console.log(todos)"
    >
      All
    </button>
  </div>
</template>

<script setup>
// @ts-nocheck
import { reactive, onBeforeMount } from "vue";
import TodoList from "./components/TodoList.vue";
import NewTodoBox from "./components/NewTodoBox.vue";

const todos = reactive([]);

onBeforeMount(() => {
  const localTodos = JSON.parse(localStorage.getItem("todos"));
  if (!!localTodos) {
    localTodos.forEach((todo) => {
      todos.push(todo);
    });
  } else {
    todos.push({ id: 0, content: "add new todo", done: false });
  }
}),
  console.log("🚀 ~ file: App.vue:35 ~ todos:", todos);
</script>

<style scoped></style>
