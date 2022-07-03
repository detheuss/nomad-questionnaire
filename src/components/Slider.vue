<template>
  <div id="slider">
    <b-container>
      <h1>Slider</h1>
      <div>
        <vue-slide-bar
          v-model="slider.value"
          :data="slider.data"
          :range="slider.range"
          :showTooltip="false"
          :lineHeight="20"
          :processStyle="setProcessStyle()"
          @callbackRange="updateRangeValue"
        />
      </div>
      <div>{{ slider.value }}</div>
      <div>{{ slider.rangeValue }}</div>
    </b-container>
  </div>
</template>

<script>
export default {
  props: {
    labels: {
      type: Array,
      default() {
        return ["Very unlikely", "Unlikely", "Neutral", "Likely", "Very likely"];
      },
    },
  },
  data() {
    return {
      simpleValue: 50,

      slider: {
        value: 0,
        data: [0, 1, 2, 3, 4],
        range: [
          { label: this.labels[0] },
          { label: this.labels[1] },
          { label: this.labels[2] },
          { label: this.labels[3] },
          { label: this.labels[4] },
        ],
        rangeValue: {},
      },
    };
  },

  methods: {
    updateRangeValue(val) {
      this.slider.value = val;
      this.slider.rangeValue = val.label;
    },

    setProcessStyle() {
      if (!this.slider) return;
      if (this.slider.value == 0) return { backgroundColor: "tomato", border: "5px solid tomato" };
      if (this.slider.value == 1) return { backgroundColor: "salmon" };
      if (this.slider.value == 2) return { backgroundColor: "#ffb347" };
      if (this.slider.value == 3) return { backgroundColor: "#77dd77" };
      if (this.slider.value == 4) return { backgroundColor: "#03c03c" };
    },
  },
};
</script>

<style lang="scss" scoped>
#slider {
  width: 100%;
}
</style>
