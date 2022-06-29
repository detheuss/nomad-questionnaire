<template>
  <div id="single-select" class="mt-3">
    <b-container>
      <h1>Single select</h1>
      <div class="single-select-container">
        <div
          v-for="(item, index) in items"
          :key="index"
          @click="select(item)"
          class="single-select-btn base-form-item"
          :class="item == selected ? 'selected' : ''"
        >
          <div class="answer-number">{{ index + 1 }}.</div>
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
      selected: "",
    };
  },

  methods: {
    select(item) {
      this.selected = item;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../definitions.scss";
#single-select {
  width: 100%;
}

.single-select-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
}
.single-select-btn {
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

.answer-number {
  margin-right: 20px;
}
</style>
