<template>
  <div class="main-wrap">
    <div class="left">
      <BoxShadowGenerator :listExample="this.listShadow" @listShadow="getListShadow"  />
    </div>
    <div class="right">
      <BoxShadowPreview :list="this.listShadow" />
      <BoxShadowCssCode :list="this.listShadow" />
      <BoxShadowExampleTemplate  @example="getListExample"/>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      listShadow: [{ name: "0px 0px 5px 3px rgba(0,0,0,0.2)", id: 0 }],
    };
  },
  methods: {
    getListShadow(list) {
      this.listShadow = list;
    },
    getListExample(lists) {
      this.listShadow = lists;
    }
  },
};
</script>

<style lang="scss" scoped>
.main-wrap {
  background-color: $gray;
  min-height: 100vh;
  display: flex;
  flex-wrap: wrap;
  padding: 20px calc(50vw - 500px);

  .left,
  .right {
    flex: 50%;
    padding: 0 10px;
  }
  @include mb {
    padding: 20px 10px;

    .left,
    .right {
      flex: 100%;
    }
  }
}
</style>
