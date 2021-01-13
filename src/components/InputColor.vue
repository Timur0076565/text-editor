<template>
  <input
    class="color-component"
    type="color"
    @change="chooseColor"
    id="myColor"
		:value="inputValue"
  />
</template>

<script>
export default {
  props: {
		inputValue: {
      type: String,
      default: "",
    },
  },
  methods: {
    chooseColor(event) {
			let mycolor = event.target.value
			this.$emit('chooseColor', mycolor)
		},
  },
};
</script>

<style scoped>
.color-component {
  width: 20px;
  height: 20px;
  cursor: pointer;
}
</style>