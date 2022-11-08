<template>
  <div class="preview">
    <div class="preview-header">
      <h2 class="preview-title">Preview</h2>
      <div class="d-flex">
        <BoxShadowColorPicker propColor="#ffffff" @color="colorBg" />
        <BoxShadowColorPicker
          class="ml-3"
          propColor="#2196f3"
          @color="colorBox"
        />
      </div>
    </div>
    <div class="preview-section" ref="previewSection">
      <span
        v-for="element in list"
        :key="element.id"
        class="preview-area"
        :style="{ boxShadow: element.name }"
      ></span>
      <div class="preview-area" ref="previewArea"></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["list"],
  data() {
    return {};
  },
  methods: {
    colorBg(color) {
      this.$refs.previewSection.style.backgroundColor = color;
    },
    colorBox(color) {
      this.$refs.previewArea.style.backgroundColor = color;
    },
  },
};
</script>

<style lang="scss" scoped>
.preview {
  background: $white;
  box-shadow: 0 0 0 1px rgba(63, 63, 68, 0.05),
    0 1px 3px 0 rgba(63, 63, 68, 0.15);
  border-radius: 4px;
  padding: 20px;

  @include mb {
    margin-top: 20px;
  }

  .preview-header {
    @include mb {
      display: block;
    }

    display: flex;
    justify-content: space-between;
    .preview-title {
      font-size: 1em;
      margin-bottom: 25px;
    }
  }

  .preview-section {
    min-height: 280px;
    padding: 40px;
    @include mb {
      display: flex;
      padding: 40px 0;
      justify-content: center;
    }
  }

  .preview-area {
    position: absolute;
    width: 200px;
    height: 200px;
  }
}
</style>
