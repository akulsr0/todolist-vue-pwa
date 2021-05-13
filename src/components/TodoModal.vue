<template>
  <div
    class="w-full h-full fixed top-0 flex justify-center bg-gray-400 bg-opacity-60"
    v-if="Object.keys(showTodo).length > 0"
  >
    <div class="bg-blue-100 w-full h-fit-content mx-4 my-40 p-2 rounded-md">
      <div class="flex flex-row items-center justify-between pr-2">
        <div class="font-semibold text-lg">{{ showTodo.todoTitle }}</div>
        <div class="text-sm" v-on:click="setShowTodo()">❌</div>
      </div>
      <div class="my-2">{{ showTodo.todoDescription }}</div>
      <div class="flex flex-col">
        <button
          class="bg-green-400 mt-1 p-1 rounded text-white font-semibold"
          v-if="!showTodo.isDone"
          v-on:click="setTodoDone(showTodo)"
        >
          Done
        </button>
        <button
          class="bg-red-400 mt-1 p-1 rounded text-white font-semibold"
          v-on:click="removeTodo(showTodo)"
        >
          Remove
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["showTodo", "setShowTodo", "setTodos"],
  methods: {
    setTodoDone(todo) {
      const todos = JSON.parse(localStorage.getItem("todos"));
      const finalTodos = [
        ...todos.filter((t) => t.id != todo.id),
        { ...todo, isDone: true },
      ];
      localStorage.setItem("todos", JSON.stringify(finalTodos));
      this.setTodos();
      this.setShowTodo();
    },
    removeTodo(todo) {
      const todos = JSON.parse(localStorage.getItem("todos"));
      const finalTodos = todos.filter((t) => t.id !== todo.id);
      localStorage.setItem("todos", JSON.stringify(finalTodos));
      this.setTodos();
      this.setShowTodo();
    },
  },
};
</script>

<style>
.h-fit-content {
  height: fit-content;
}
</style>