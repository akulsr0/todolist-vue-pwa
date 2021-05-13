<template>
  <div
    class="w-full h-full fixed top-0 flex justify-center bg-gray-400 bg-opacity-60"
    v-if="showNewTodoModal"
  >
    <div class="bg-blue-100 w-full h-fit-content mx-4 my-40 p-2 rounded-md">
      <div class="flex flex-row justify-between items-center pr-2">
        <span class="text-xl font-semibold">Add new Todo</span>
        <span class="text-sm" v-on:click="setShowNewTodoModal(false)">❌</span>
      </div>
      <div class="mt-2">
        <input
          type="text"
          placeholder="Title"
          class="w-full p-1"
          v-model="todoTitle"
        />
        <textarea
          placeholder="Details"
          class="mt-2 h-32 w-full p-1"
          v-model="todoDescription"
        ></textarea>
      </div>
      <div class="flex flex-row justify-end mt-1">
        <button
          class="bg-blue-400 ml-2 px-2 py-1 rounded text-white font-semibold"
          v-on:click="setShowNewTodoModal(false)"
        >
          Cancel
        </button>
        <button
          class="bg-blue-500 ml-2 px-2 py-1 rounded text-white font-semibold"
          v-on:click="addTodo"
        >
          Add
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["showNewTodoModal", "setShowNewTodoModal", "setTodos", "setShowDone"],
  data() {
    return { todoTitle: "", todoDescription: "" };
  },
  methods: {
    resetInputField() {
      this.todoTitle = "";
      this.todoDescription = "";
    },
    addTodo() {
      const _todos = JSON.parse(localStorage.getItem("todos"));
      const todo = {
        id: Date.now(),
        todoTitle: this.todoTitle,
        todoDescription: this.todoDescription,
        isDone: false,
      };
      const todos = _todos ? [..._todos, todo] : [todo];
      localStorage.setItem("todos", JSON.stringify(todos));
      this.setTodos();
      this.setShowNewTodoModal(false);
      this.resetInputField();
      this.setShowDone(false);
    },
  },
};
</script>

<style>
.h-fit-content {
  height: fit-content;
}
</style>