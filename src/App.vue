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

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
