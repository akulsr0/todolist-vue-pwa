<template>
  <div class="h-14 w-full bg-blue-500 fixed bottom-0 flex flex-row">
    <div
      class="flex-1 flex items-center justify-center"
      v-on:click="setShowDone(false)"
    >
      <h1 class="text-xl font-bold text-white">Todo's</h1>
    </div>
    <div
      class="flex-1 flex items-center justify-center"
      v-on:click="setShowDone()"
    >
      <h1 class="text-xl font-bold text-white">Done</h1>
    </div>
  </div>
</template>

<script>
export default {
  props: ["setShowDone"],
};
</script>

<style>
</style>