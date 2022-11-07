<template>
  <div>
    <div
      class="color-picker"
      ref="colorPicker"
      @click="showColorPicker = !showColorPicker"
    ></div>
    <div
      class="color-picker-modal"
      v-show="showColorPicker"
      v-click-outside="onClickOutside"
    >
      <v-color-picker
        swatches-max-height="200"
        v-model="color"
      ></v-color-picker>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.color-picker {
  height: 28px;
  width: 44px;
  border-radius: 4px;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 10px 36px 0px,
    rgba(0, 0, 0, 0.06) 0px 0px 0px 1px;
  border: 2px solid $gray;
}

.color-picker-modal {
  position: absolute;
  margin-top: 10px;
  z-index: 1;
}
</style>

<script>
export default {
  props: ['propColor'],
  data() {
    return {
      color: "#000000",
      showColorPicker: false,
      checkOnClickOutside: false,
    };
  },
  watch: {
    color(newValue) {
      this.checkOnClickOutside = true;
      this.setBgColorPicker();
      this.$emit("color", newValue);
    },
  },
  mounted() {
    this.setBgColorPicker();
    this.color = this.propColor;
  },
  methods: {
    setBgColorPicker() {
      this.$refs.colorPicker.style.backgroundColor = this.color;
    },
    onClickOutside() {
      if (this.checkOnClickOutside) {
        this.showColorPicker = false;
        this.checkOnClickOutside = false;
      }
    },
  },
};
</script>
