<template>
  <div id="app">
    <Index />
  </div>
</template>

<script>
import Index from "./components/Index.vue";

export default {
  name: "app",
  components: {
    Index,
  },
};
</script>

<style>
body {
  user-select: none;
  font-family: "VT323", monospace;
  color: yellowgreen;
  background-color: black;
}
</style>
