<template>
  <div id="dropdown-search" class="mt-3">
    <b-container>
      <h1>Dropdown search</h1>

      <v-select
        :options="dummyData"
        :clearable="false"
        placeholder="Start typing to filter..."
        class="dropdown-search"
        :class="isMaxSelectExceeded ? 'validation-warning-border' : ''"
        @input="select"
      ></v-select>

      <div v-if="isMaxSelectExceeded" class="validation-warning">
        Please select max {{ this.maxSelect }} items
      </div>
      <div class="selected-items-container mt-3">
        <div
          class="selected-item base-form-item"
          v-for="(item, index) in selected"
          :key="index"
          @click="deselect(index)"
        >
          <div>
            {{ item }}
          </div>
          <div>
            <b-icon-x-circle />
          </div>
        </div>
      </div>
    </b-container>
  </div>
</template>

<script>
import "vue-select/dist/vue-select.css";
import { dummyData } from "../assets/dummyData.js";
export default {
  data() {
    return {
      dummyData: dummyData,
      selected: [],
      isMaxSelectExceeded: false,
    };
  },

  props: {
    maxSelect: {
      type: Number,
      default: 3,
    },
  },

  methods: {
    checkExceedsMaxSelect() {
      if (this.selected.length > this.maxSelect) {
        this.isMaxSelectExceeded = true;
      } else {
        this.isMaxSelectExceeded = false;
      }
    },

    select(val) {
      if (this.selected.includes(val)) return;
      this.selected.push(val);
      this.checkExceedsMaxSelect();
    },

    deselect(index) {
      this.selected.splice(index, 1);
      this.checkExceedsMaxSelect();
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../definitions.scss";

#dropdown-search {
  display: flex;
  width: 100%;
}

.dropdown-search {
  border: 2px solid $base-color;
}

.selected-items-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  text-align: center;
}

.selected-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  height: fit-content;
  width: 100%;
  border: 2px solid $base-color;
  flex: 1;

  transition: 0.2s ease-in-out;
  border-radius: 16px;
  @media (min-width: $desktop) {
    width: 100%;
  }
}

.selected-item:hover {
  cursor: pointer;
  border: 2px solid $base-color;
  background-color: $base-color;
  color: white;
}
</style>
