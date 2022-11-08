<template>
  <div class="generator">
    <h2 class="generator-title">Box-Shadow CSS Generator</h2>
    <div class="input-slider" v-for="item in silderData" :key="item.key">
      <p>{{ item.name }}</p>
      <v-slider
        color="#5c6ac4"
        v-model="item.value"
        step="1"
        :min="item.min"
        :max="item.max"
        thumb-label
      ></v-slider>
    </div>

    <v-checkbox v-model="checkbox" color="#5c6ac4" class="mt-0 pt-0">
      <template v-slot:label>
        <span style="font-size: 0.8rem">Inset</span>
      </template>
    </v-checkbox>

    <BoxShadowColorPicker @color="getColor" propColor="#000000" />

    <div class="layer">
      <v-divider></v-divider>
      <v-btn small class="btn" @click="addLayer">Add Layer </v-btn>
      <draggable
        :list="list"
        :move="checkMove"
        @start="dragging = true"
        @end="dragEnd()"
      >
        <div
          class="item"
          v-for="(element, index) in list"
          :class="{ active: index === activeItem }"
          :key="element.id"
          @click="clickItem(index)"
        >
          <div>
            <v-icon small>mdi-dots-vertical </v-icon>
            {{ element.name }}
          </div>
          <div style="cursor: pointer">
            <v-icon small>mdi-pencil </v-icon>
            <span @click="removeItem(index)"
              ><v-icon small>mdi-delete </v-icon></span
            >
          </div>
        </div>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
let id = 1;
export default {
  components: {
    draggable,
  },
  props: ["listExample"],
  data() {
    return {
      silderData: [
        { name: "Shift right", min: -50, max: 50, value: 0, key: "shiftRight" },
        { name: "Shift down", min: -50, max: 50, value: 0, key: "shiftDown" },
        { name: "Spread", min: 0, max: 100, value: 3, key: "spread" },
        { name: "Blur", min: 0, max: 100, value: 5, key: "blur" },
        { name: "Opacity", min: 0, max: 100, value: 20, key: "opacity" },
      ],
      checkbox: false,
      list: [{ name: "0px 0px 5px 3px rgba(0,0,0,0.2)", id: 0 }],
      dragging: false,
      activeItem: 0,
      activeItemFuture: 0,
      colorValue: "0,0,0",
    };
  },
  watch: {
    silderData: {
      handler(newValue, oldValue) {
        this.formatToCSS();
      },
      deep: true,
    },
    colorValue(newValue) {
      this.formatToCSS();
    },
    checkbox(newValue) {
      this.formatToCSS();
    },
    list: {
      handler(newValue, oldValue) {
        this.$emit("listShadow", newValue);
      },
      deep: true,
    },
    listExample(newValue) {
      id = newValue.length
      this.list = newValue;
    },
  },
  methods: {
    getColor(color) {
      this.colorValue = this.hexToRgbA(color);
    },
    addLayer() {
      this.list.push({ name: "0px 0px 5px 3px rgba(0,0,0,0.2)", id: id++ });
    },
    removeItem(index) {
      if (this.list.length > 1) {
        this.list.splice(index, 1);
      }
    },
    checkMove(e) {
      this.activeItemFuture = e.draggedContext.futureIndex;
    },
    clickItem(index) {
      this.activeItem = index;
    },
    dragEnd() {
      this.dragging = false;
      this.activeItem = this.activeItemFuture;
    },
    formatToCSS() {
      let css =
        this.getValueBySilderDataKey("shiftRight")[0].value +
        "px " +
        this.getValueBySilderDataKey("shiftDown")[0].value +
        "px " +
        this.getValueBySilderDataKey("blur")[0].value +
        "px " +
        this.getValueBySilderDataKey("spread")[0].value +
        "px " +
        "rgba(" +
        this.colorValue +
        "," +
        Number(this.getValueBySilderDataKey("opacity")[0].value) / 100 +
        ")";
      if (this.checkbox) {
        css = css + " inset";
      }
      this.list[this.activeItem].name = css;
    },
    getValueBySilderDataKey(key) {
      return this.silderData.filter((data) => data.key === key);
    },
    hexToRgbA(hex) {
      let c;
      if (/^#([A-Fa-f0-9]{3}){1,2}$/.test(hex)) {
        c = hex.substring(1).split("");
        if (c.length == 3) {
          c = [c[0], c[0], c[1], c[1], c[2], c[2]];
        }
        c = "0x" + c.join("");
        return [(c >> 16) & 255, (c >> 8) & 255, c & 255].join(",");
      }
      throw new Error("Bad Hex");
    },
  },
};
</script>

<style lang="scss" scoped>
.generator {
  background: $white;
  box-shadow: 0 0 0 1px rgba(63, 63, 68, 0.05),
    0 1px 3px 0 rgba(63, 63, 68, 0.15);
  border-radius: 4px;
  padding: 20px;

  .generator-title {
    font-size: 1em;
    margin-bottom: 25px;
  }

  .input-slider {
    p {
      margin-bottom: 4px;
      font-size: 0.8rem;
    }
  }

  .layer {
    margin-top: 20px;
    .btn {
      margin-top: 20px;
      margin-bottom: 20px;
    }
    .item {
      &.active {
        background-color: $violet;
        color: $white;
        i {
          color: $white;
        }
      }
      cursor: move;
      padding: 6px;
      display: flex;
      justify-content: space-between;
      border-radius: 4px;
      margin: 10px 0;
    }
  }
}
</style>
