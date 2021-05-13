<template>
  <div
    class="bg-blue-100 mb-2 px-2 py-1 flex flex-row items-center rounded-md"
    v-on:click="setShowTodo(todo)"
  >
    <span>{{ todo.isDone ? "✅" : "📌" }}</span>
    <h3 class="ml-4">{{ todo.todoTitle }}</h3>
  </div>
</template>

<script>
export default {
  props: ["todo", "setShowTodo"],
};
</script>

<style>
</style>