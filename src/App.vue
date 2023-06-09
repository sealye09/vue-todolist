<template>
  <div class="flex flex-col items-center justify-center w-full">
    <div class="w-full flex flex-col px-8 py-4">
      <div class="w-full text-3xl py-4">Todo</div>

      <NewTodoBox :todos="todos" />

      <TodoList :todos="todos" />
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import TodoList from "./components/TodoList.vue";
import NewTodoBox from "./components/NewTodoBox.vue";

const todos = reactive([
  {
    id: 1,
    content: "todo1",
    done: false,
  },
  {
    id: 2,
    content: "todo2",
    done: true,
  },
  {
    id: 3,
    content: "todo3",
    done: false,
  },
]);
console.log("🚀 ~ file: App.vue:35 ~ todos:", todos);
</script>

<style scoped></style>
