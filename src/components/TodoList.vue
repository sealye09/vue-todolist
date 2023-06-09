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
      :handleEdit="() => handleEdit(todo.id)"
    />
  </ul>
</template>

<script setup>
// @ts-nocheck
import { ref } from "vue";
import TodoItem from "./TodoItem.vue";

const props = defineProps({
  todos: Array,
});
console.log("🚀 ~ file: TodoList.vue:22 ~ todos:", props.todos);

const editIndex = ref(1);

const handleDelete = (id) => {
  const index = props.todos.findIndex((todo) => todo.id === id);
  props.todos.splice(index, 1);
  localStorage.setItem("todos", JSON.stringify(props.todos));
};

const handleEdit = (id) => {
  console.log("🚀 ~ file: TodoList.vue:37 ~ handleEdit ~ editIndex:", editIndex.value);
  const index = props.todos.findIndex((todo) => todo.id === id);
  const newContent = prompt("Edit todo", props.todos[index].content);
  if (newContent !== null) {
    props.todos[index].content = newContent;
    localStorage.setItem("todos", JSON.stringify(props.todos));
  }
};
</script>

<style scoped></style>
