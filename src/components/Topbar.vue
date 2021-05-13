<template>
  <div class="w-full bg-blue-500 h-14 flex items-center justify-between px-3">
    <h1
      class="text-2xl text-white font-semibold"
      v-on:click="setShowAbout(true)"
    >
      Todo List
    </h1>
    <span class="text-2xl" v-on:click="setShowNewTodoModal">📝</span>
  </div>
</template>

<script>
export default {
  props: ["setShowNewTodoModal", "setShowAbout"],
};
</script>

<style>
</style>