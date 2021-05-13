<template>
  <div
    class="w-full h-full fixed top-0 flex justify-center bg-gray-400 bg-opacity-60"
    v-if="showAbout"
  >
    <div class="bg-blue-100 w-full h-fit-content mx-4 my-40 p-2 rounded-md">
      <div class="flex flex-row items-center justify-between pr-2">
        <div class="font-semibold text-lg">TodoList</div>
        <div class="text-sm" v-on:click="setShowAbout(false)">❌</div>
      </div>
      <div class="mt-2 font-light text-sm">
        Made with&nbsp;❤️&nbsp;&nbsp;and Vue.js <br />
        by Akul Srivastava
      </div>
      <div class="flex flex-row text-sm mt-2">
        <span
          class="bg-blue-300 flex-1 flex items-center justify-center p-1 rounded mr-1 font-semibold"
          v-on:click="openGithub()"
          >Github</span
        >
        <span
          class="bg-blue-300 flex-1 flex items-center justify-center p-1 rounded ml-1 font-semibold"
          v-on:click="openPlaystore()"
          >PlayStore</span
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["showAbout", "setShowAbout"],
  methods: {
    openGithub() {
      window.open("https://github.com/akulsr0", "_blank");
    },
    openPlaystore() {
      window.open(
        "https://play.google.com/store/apps/developer?id=Akul+Srivastava",
        "_blank"
      );
    },
  },
};
</script>

<style>
</style>