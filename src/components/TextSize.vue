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
      {{ fontSizeOption }}
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
      selected: "12px",
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
	height: 24px;
	outline: none;
	border: none;
}
</style>