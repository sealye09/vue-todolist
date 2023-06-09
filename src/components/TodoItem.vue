<template>
  <li class="flex gap-2">
    <span
      class="grow px-2"
      :class="props.done && 'text-gray-400 line-through'"
    >
      {{ props.content }}
    </span>
    <button
      @click="props.handleEdit"
      class="h-full bg-blue-400 hover:bg-blue-500 text-white font-bold px-4 rounded-md"
    >
      Edit
    </button>
    <button
      @click="props.toggleDone"
      class="h-full hover:bg-blue-500 text-white font-bold px-4 rounded-md"
      :class="props.done ? 'bg-blue-200' : 'bg-blue-400'"
    >
      ✓
    </button>
    <button
      @click="props.handleDelete"
      class="h-full bg-blue-400 hover:bg-blue-500 text-white font-bold px-4 rounded-md"
    >
      ✕
    </button>
  </li>
</template>

<script setup>
const props = defineProps({
  content: String,
  done: Boolean,
  handleEdit: Function,
  toggleDone: Function,
  handleDelete: Function,
});
</script>

<style scoped></style>
