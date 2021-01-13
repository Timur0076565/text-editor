<template>
  <div id="app">
    <TextEditor />
  </div>
</template>

<script>
import TextEditor from "./views/TextEditor.vue";

export default {
  name: "App",
  components: {
    TextEditor,
  },
};
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  max-width: 500px;
  margin: 0 auto;
}
</style>
