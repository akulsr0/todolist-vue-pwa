<template>
  <div class="m-2">
    <Todo
      v-for="(todo, i) in todos"
      v-bind:key="i"
      :todo="todo"
      :setShowTodo="setShowTodo"
    />
  </div>
</template>

<script>
import Todo from "./Todo";
export default {
  props: ["todos", "setShowTodo"],
  components: {
    Todo,
  },
};
</script>

<style>
</style>