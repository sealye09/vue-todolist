<template>
  <div class="flex gap-2 h-8 px-2 my-8">
    <input
      class="h-full w-full px-2 border-2 border-gray-300 rounded-md focus:outline-none focus:border-blue-500"
      type="text"
      placeholder="new todo"
      v-model="newTodo"
      @keydown="handleInput"
    />
    <button
      @click="handleAdd"
      class="h-full bg-blue-500 hover:bg-blue-700 text-white font-bold px-4 rounded-md"
    >
      +
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  todos: Array,
});
console.log("🚀 ~ file: NewTodoBox.vue:25 ~ todos:", props.todos);

const newTodo = ref("");

const handleAdd = () => {
  console.log("handleAdd");
  props.todos?.push({
    id: props.todos.length + 1,
    content: newTodo.value,
    done: false,
  });
  newTodo.value = "";
  localStorage.setItem("todos", JSON.stringify(props.todos));
};

const handleInput = (event) => {
  if (event.key === "Enter") {
    handleAdd();
  }
};
</script>

<style scoped></style>
