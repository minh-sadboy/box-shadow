<template>
  <div class="preview">
    <div class="preview-header">
      <h2 class="preview-title">Preview</h2>
      <div class="d-flex">
        <BoxShadowColorPicker propColor="#ffffff" />
        <BoxShadowColorPicker class="ml-3" propColor="#2196f3" />
      </div>
    </div>
    <div class="preview-section">
      <div class="preview-area"></div>
    </div>
  </div>
</template>

<script>
export default {};
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
    padding: 40px;
  }

  .preview-area {
    width: 200px;
    height: 200px;
    background-color: aqua;
  }
}
</style>
