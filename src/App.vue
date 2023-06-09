<template>
  <div class="todos h-screen w-full flex flex-col items-center my-20">
    <div class="text-3xl my-8">Todo</div>
    <div class="flex gap-2 h-8 items-center justify-center">
      <input
        class="h-full px-2 border-2 border-gray-300 rounded-md focus:outline-none focus:border-blue-500"
        type="text"
        placeholder="new todo"
        v-model="newTodo"
        @keydown="handleInput"
      />
      <button
        @click="handleAdd"
        class="h-full bg-blue-500 hover:bg-blue-700 text-white font-bold px-4 rounded-md"
      >
        Add
      </button>
    </div>

    <ul class="flex flex-col justify-center w-full">
      <li
        v-for="item in todos"
        :key="item.id"
      >
        {{ item.content }}
        <!-- <input type="checkbox" /> -->
        <input
          type="checkbox"
          v-model="item.done"
        />
      </li>
    </ul>
  </div>
</template>

<script setup>
// @ts-nocheck
import { ref } from "vue";
const newTodo = ref("");

const todos = ref([
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

const handleAdd = () => {
  console.log("handleAdd");
  todos.value.push({
    id: todos.value.length + 1,
    content: newTodo.value,
    done: false,
  });
  newTodo.value = "";
};

const handleInput = (event) => {
  if (event.key === "Enter") {
    handleAdd();
  }
};
</script>

<style scoped></style>
