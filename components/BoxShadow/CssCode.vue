<template>
  <div class="csscode">
    <div class="csscode-header">
      <h2 class="csscode-title">CSS code</h2>
    </div>
    <div class="csscode-section">
      <code> box-shadow: {{ cssCodeData }}; </code>
    </div>
  </div>
</template>

<script>
export default {
  props: ["list"],
  data() {
    return {
      cssCodeData: "0px 0px 5px 3px rgba(0,0,0,0.2)",
    };
  },
  watch: {
    list: {
      handler(newValue, oldValue) {
        let cssCode = ''
        newValue.forEach((element) => {
          cssCode = cssCode + element.name 
        });
        this.cssCodeData = cssCode
      },
      deep: true,
    },
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
.csscode {
  background: $white;
  box-shadow: 0 0 0 1px rgba(63, 63, 68, 0.05),
    0 1px 3px 0 rgba(63, 63, 68, 0.15);
  border-radius: 4px;
  padding: 20px;
  margin-top: 20px;

  .csscode-header {
    .csscode-title {
      font-size: 1em;
      margin-bottom: 25px;
    }
  }
}
</style>
