<template>
  <topbar
    :setShowNewTodoModal="setShowNewTodoModal"
    :setShowAbout="setShowAbout"
  />
  <todo-list
    :todos="
      showDone ? todos.filter((t) => t.isDone) : todos.filter((t) => !t.isDone)
    "
    :setShowTodo="setShowTodo"
  />
  <new-todo
    :showNewTodoModal="showNewTodoModal"
    :setShowNewTodoModal="setShowNewTodoModal"
    :setTodos="setTodos"
    :setShowDone="setShowDone"
  />
  <todo-modal
    :showTodo="showTodo"
    :setShowTodo="setShowTodo"
    :setTodos="setTodos"
  />
  <about :showAbout="showAbout" :setShowAbout="setShowAbout" />
  <bottom-panel :setShowDone="setShowDone" />
</template>

<script>
document.title = "Todo App";
import Topbar from "./components/Topbar";
import NewTodo from "./components/NewTodo";
import TodoList from "./components/TodoList";
import TodoModal from "./components/TodoModal";
import BottomPanel from "./components/BottomPanel";
import About from "./components/About";

export default {
  name: "App",
  data() {
    return {
      todos: [],
      showDone: false,
      showNewTodoModal: false,
      showTodo: {},
      showAbout: false,
    };
  },
  methods: {
    setShowDone(showDone = true) {
      this.showDone = showDone;
    },
    setShowNewTodoModal(showNewTodoModal = true) {
      this.showNewTodoModal = showNewTodoModal;
    },
    setShowTodo(showTodo = {}) {
      this.showTodo = showTodo;
    },
    setTodos() {
      const todos = JSON.parse(localStorage.getItem("todos"));
      if (todos) {
        this.todos = todos;
      }
    },
    setShowAbout(showAbout) {
      this.showAbout = showAbout;
    },
  },
  beforeMount() {
    this.setTodos();
  },
  components: {
    topbar: Topbar,
    "bottom-panel": BottomPanel,
    "todo-list": TodoList,
    "new-todo": NewTodo,
    "todo-modal": TodoModal,
    about: About,
  },
};
</script>


    BottomPanel<style>
</style>
