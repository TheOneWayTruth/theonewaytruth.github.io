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
    Index
  }
};
</script>

<style>
body {
  cursor: url("./assets/cursor.png") 2 2, auto;
  user-select: none;
  font-family: "VT323", monospace;
  color: yellowgreen;
  background-color: black;
}
</style>
