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

    <BoxShadowColorPicker @color="getColor" />

    <div class="layer">
      <v-divider></v-divider>
      <v-btn small class="btn" @click="addLayer">Layer </v-btn>
      <draggable
        :list="list"
        :move="checkMove"
        @start="dragging = true"
        @end="dragging = false"
      >
        <div class="item" v-for="element in list" :key="element.name">
          <v-icon small>mdi-dots-vertical </v-icon>

          {{ element.name }}
          <v-icon small>mdi-pencil </v-icon>
          <v-icon small>mdi-delete </v-icon>
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
  data() {
    return {
      silderData: [
        { name: "Shift right", min: -50, max: 50, value: 0, key: "shiftRight" },
        { name: "Shift down", min: -50, max: 50, value: 0, key: "shiftDown" },
        { name: "Spread", min: 0, max: 100, value: 3, key: "spread" },
        { name: "Blur", min: 0, max: 100, value: 3, key: "blur" },
        { name: "Opacity", min: 0, max: 100, value: 20, key: "opacity" },
      ],
      checkbox: false,
      list: [
        { name: "John", id: 0 },
        // { name: "Joao", id: 1 },
        // { name: "Jean", id: 2 },
      ],
      dragging: false,
    };
  },
  methods: {
    getColor(color) {
      console.log(color);
    },
    addLayer() {
      this.list.push({ name: "Juan " + id, id: id++ });
    },
    checkMove(e) {
      window.console.log("Future index: " + e.draggedContext.futureIndex);
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
      background-color: brown;
      i {
        color: aliceblue;
      }
    }
  }
}
</style>
