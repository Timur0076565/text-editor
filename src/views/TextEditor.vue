<template>
  <div class="text-editor" @keypress.enter="addNewText">
    <InputColor
      @chooseColor="chooseTextColor"
      :inputValue="colorTextValue"
    />
    <TextSize
      @changeFontSize="changeFontSize"
      :fontSizeOptions="fontSizeOptions"
    />
    <InputColor
      @chooseColor="chooseBgColor"
      :inputValue="colorBgValue"
    />
    <TextField @getTextFieldValue="getTextFieldValue" />
    <hr />
    <div class="list" v-for="(string, index) in list" :key="index">
      {{ string }}
    </div>
  </div>
</template>

<script>
import InputColor from "../components/InputColor.vue";
import TextSize from "../components/TextSize.vue";
import TextField from "../components/TextField.vue";

export default {
  name: "textEditor",
  components: {
    InputColor,
    TextSize,
    TextField,
  },
  data() {
    return {
      fontSizeOptions: [
        "1",
        "2",
        "3",
        "4",
        "3",
        "4",
        "5",
        "6",
        "7",
        "8",
        "9",
        "10",
      ],
      list: [
        {
          text: "My lovely",
          fontSize: "12px",
          color: "red",
        },
        {
          text: "little",
          fontSize: "16px",
          color: "pink",
        },
      ],
      colorTextValue: null,
      fontSizeValue: null,
      colorBgValue: null,
      textValue: null,
    };
	},
	// computed: {
	// 	filteredList() {
	// 		return this.list.filter(item => item.text || item.fontSize || item.color || item.backgroundColor !== null)
	// 	}
	// },
  methods: {
    chooseTextColor(value) {
			document.execCommand("foreColor", false, value)
      this.colorTextValue = value;
    },
    changeFontSize(value) {
			document.execCommand("fontSize", false, value)
      this.fontSizeValue = value;
    },
    chooseBgColor(value) {
			document.execCommand("backColor", false, value)
      this.colorBgValue = value;
    },
    getTextFieldValue(value) {
      this.textValue = value;
    },
    addNewText() {
      this.list.push({
        text: this.textValue,
        fontSize: this.fontSizeValue,
        color: this.colorTextValue,
        backgroundColor: this.colorBgValue,
      });
    },
  },
};
</script>

<style scoped>
.text-editor {
}
</style>