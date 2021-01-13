<template>
  <div class="text-editor">
    <div class="text-editor-wrapper">
      <div class="text-editor-btns">
        <div class="text-editor-btn">
          color:
          <InputColor
            @chooseColor="chooseTextColor"
            :inputValue="colorTextValue"
            title="color"
          />
        </div>
        <div class="text-editor-btn">
          font size:
          <TextSize
            @changeFontSize="changeFontSize"
            :fontSizeOptions="fontSizeOptions"
          />
        </div>
        <div class="text-editor-btn">
          background:
          <InputColor
            @chooseColor="chooseBgColor"
            :inputValue="colorBgValue"
            title="background"
          />
        </div>
      </div>
      <TextField @getTextFieldValue="getTextFieldValue" ref="textField" />
    </div>
    <hr />
    <div class="list" v-for="(string, index) in list" :key="index">
      <div
        :style="{
          color: string.color,
          fontSize: string.fontSize,
          backgroundColor: string.backgroundColor,
        }"
      >
        {{ string.text }}
      </div>
      ({{ string }})
      <hr />
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
        "12px",
        "14px",
        "16px",
        "18px",
        "20px",
        "22px",
        "24px",
        "26px",
        "28px",
        "30px",
        "32px",
        "34px",
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
  methods: {
    chooseTextColor(value) {
      document.execCommand("foreColor", false, value);
      this.colorTextValue = value;
    },
    changeFontSize(value) {
      document.execCommand("fontSize", false, value);
      const fontElements = window.getSelection().anchorNode.parentNode;
      fontElements.removeAttribute("size");
      fontElements.style.fontSize = value;
      this.fontSizeValue = value;
    },
    chooseBgColor(value) {
      document.execCommand("backColor", false, value);
      this.colorBgValue = value;
    },
    getTextFieldValue(value) {
      this.textValue = value;
      const text =
        this.textValue !== null
          ? {
              text: this.textValue,
            }
          : {};
      const fontSize =
        this.fontSizeValue !== null
          ? {
              fontSize: this.fontSizeValue,
            }
          : {};
      const color =
        this.colorTextValue !== null
          ? {
              color: this.colorTextValue,
            }
          : {};
      const backgroundColor =
        this.colorBgValue !== null
          ? {
              backgroundColor: this.colorBgValue,
            }
          : {};
      const newObj = { ...text, ...fontSize, ...color, ...backgroundColor };
      if (this.textValue !== "") this.list.push(newObj);
      this.colorTextValue = null;
      this.fontSizeValue = null;
      this.colorBgValue = null;
      this.textValue = null;
    },
  },
};
</script>

<style scoped>
.text-editor-btns {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.text-editor-btn {
	border: 1px solid black;
	border-bottom: none;
	width: 100%;
	padding: 0 15px;
}
</style>