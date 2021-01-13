<template>
  <div class="text-field-component" contenteditable="true" ref="textField" @keypress.enter="getTextFieldValue"></div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
    };
  },
  methods: {
    getTextFieldValue() {
      this.$emit('getTextFieldValue', this.$refs.textField.innerText)
      this.$refs.textField.innerText = null
    }
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
