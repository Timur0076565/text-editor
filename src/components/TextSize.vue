<template>
  <select
    class="text-size-component"
    @change="changeFontSize()"
    v-model="selected"
  >
    <option
      v-for="(fontSizeOption, index) in fontSizeOptions"
      :key="index"
      :value="fontSizeOption"
    >
      {{ fontSizeOption }}px
    </option>
  </select>
</template>

<script>
export default {
  props: {
    fontSizeOptions: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {
      selected: "10",
    };
  },
  methods: {
    changeFontSize() {
			this.$emit("changeFontSize", this.selected);
    },
  },
};
</script>

<style scoped>
.text-size-component {
  min-width: 55px;
	height: 30px;
	outline: none;
}
</style>