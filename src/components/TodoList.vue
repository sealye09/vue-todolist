<template>
  <ul class="flex flex-col justify-center w-full gap-2">
    <TodoItem
      v-for="todo in props.todos"
      class="mx-2"
      key="todo.id"
      :content="todo.content"
      :done="todo.done"
      :toggleDone="() => (todo.done = !todo.done)"
      :handleDelete="() => handleDelete(todo.id)"
    />
  </ul>
</template>

<script setup>
// @ts-nocheck
import TodoItem from "./TodoItem.vue";

const props = defineProps({
  todos: Array,
});
console.log("🚀 ~ file: TodoList.vue:22 ~ todos:", props.todos);

const handleDelete = (id) => {
  const index = props.todos.findIndex((todo) => todo.id === id);
  props.todos.splice(index, 1);
};
</script>

<style scoped></style>
