<template>
  <div class="text-field-component-wrapper">
    <div
      class="text-field-component"
      contenteditable="true"
      ref="textField"
    ></div>
    <Button @click.native="getTextFieldValue" />
  </div>
</template>

<script>
import Button from "../components/Button.vue";

export default {
  components: {
    Button,
  },
  data() {
    return {
      text: "",
    };
  },
  methods: {
    getTextFieldValue() {
      this.$emit("getTextFieldValue", this.$refs.textField.innerText);
      this.$refs.textField.innerText = null;
    },
  },
};
</script>

<style scoped>
.text-field-component {
  border: 1px solid black;
  display: block;
  width: 500px;
  min-height: 200px;
  outline: none;
  padding: 10px;
}
</style>
