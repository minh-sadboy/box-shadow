<template>
  <div class="main-wrap">
    <div class="left">
      <BoxShadowGenerator />
    </div>
    <div class="right">f</div>
  </div>
</template>

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
