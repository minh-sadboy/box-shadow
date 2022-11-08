<template>
  <div class="example">
    <div class="example-header">
      <h2 class="example-title">Template</h2>
    </div>
    <div class="example-section">
      <div @click="exampleClick(1)">
        <span
          class="example-area"
          v-for="element in example1"
          :key="element.id"
          :style="{ boxShadow: element.name }"
        ></span>
        <div class="example-area"></div>
      </div>
      <div style="margin-left: 100px" @click="exampleClick(2)">
        <span
          class="example-area"
          v-for="element in example2"
          :key="element.id"
          :style="{ boxShadow: element.name }"
        ></span>
        <div class="example-area"></div>
      </div>
    </div>
  </div>
</template>

<script>
const listExample1 = [
  { name: "rgba(225,238,255,1) 25px 25px 0px 0px", id: 0},
  { name: "rgba(202,230,255,1) 20px 20px 0px 0px", id: 1 },
  { name: "rgba(161,216,255,1) 15px 15px 0px 0px", id: 2 },
  { name: "rgba(95,184,255,1) 10px 10px 0px 0px", id: 3 },
  { name: "rgba(40,159,237,1) 5px 5px 0px 0px", id: 4 },
];

const listExample2 = [
  { name: "rgba(255,0,0,1) -18px 0px 40px 0px", id: 0 },
  { name: "rgba(255,128,0,1) -10px 0px 20px 0px", id: 1 },
  { name: "rgba(255,255,0,1) -2px 0px 10px 0px", id: 2 },
  { name: "rgba(255,255,255,1) -1px 0px 4px 0px", id: 3 },
];
export default {
  data() {
    return {
      example1: listExample1,
      example2: listExample2,
    };
  },
  methods: {
    exampleClick(i) {
      if (i === 1) {
        this.$emit("example", listExample1);
      }
      if (i === 2) {
        this.$emit("example", listExample2);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.example {
  background: $white;
  box-shadow: 0 0 0 1px rgba(63, 63, 68, 0.05),
    0 1px 3px 0 rgba(63, 63, 68, 0.15);
  border-radius: 4px;
  padding: 20px;
  margin-top: 20px;

  .example-header {
    .example-title {
      font-size: 1em;
      margin-bottom: 25px;
    }
  }

  .example-section {
    min-height: 90px;
    padding: 10px;
  }

  .example-area {
    position: absolute;
    width: 50px;
    height: 50px;
    cursor: pointer;
    background-color: $blue;
    &:hover {
      border: $violet solid 2px;
    }
  }
}
</style>
