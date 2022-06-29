<template>
  <div id="multi-select" class="mt-3">
    <b-container>
      <h1>Multi select</h1>
      <div class="multi-select-container">
        <div
          v-for="(item, index) in items"
          :key="index"
          @click="updateSelected(item)"
          class="multi-select-btn base-form-item"
          :class="selected.includes(item) ? 'selected' : ''"
        >
          <div class="answer-checkbox">
            <b-icon v-if="!selected.includes(item)" icon="square" />
            <b-icon v-else icon="check-square" />
          </div>
          <div>{{ item }}</div>
        </div>
      </div>

      <div>
        {{ selected }}
      </div>
    </b-container>
  </div>
</template>

<script>
import { dummyData } from "../assets/dummyData.js";
export default {
  data() {
    return {
      items: dummyData,
      selected: [],
    };
  },

  methods: {
    updateSelected(item) {
      if (!this.selected.includes(item)) this.selected.push(item);
      else {
        this.selected = this.selected.filter((i) => i != item);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../definitions.scss";

#multi-select {
  width: 100%;
}
.multi-select-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
}
.multi-select-btn {
  display: flex;
  flex-direction: row;

  width: 100%;

  border: 2px solid $base-color;
  cursor: pointer;

  transition: 0.2s ease-in-out;

  &:hover {
    background-color: $base-color;
    color: white;
  }
}

.selected {
  background-color: $base-color;
  color: white;
}

.answer-checkbox {
  margin-right: 20px;
}
</style>
