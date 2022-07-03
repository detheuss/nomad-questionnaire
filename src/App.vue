<template>
  <div id="app">
    <!-- Dropdown with search -->
    <DropdownSearch :max-select="3" />

    <!-- Single select -->
    <SingleSelect />
    <!-- Multi select -->
    <MultiSelect />

    <!-- Slider -->
    <Slider />
    <Slider />
    <Slider />
    <!-- Vertical single select -->
  </div>
</template>

<script>
import DropdownSearch from "./components/DropdownSearch.vue";
import SingleSelect from "./components/SingleSelect.vue";
import MultiSelect from "./components/Multiselect.vue";
import Slider from "./components/Slider.vue";
export default {
  name: "App",
  components: { DropdownSearch, SingleSelect, MultiSelect, Slider },
};
</script>

<style lang="scss">
@import "./definitions.scss";

:root {
  --vs-dropdown-option--active-bg: blueviolet;
}

html {
}
#app {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: $base-black;
  max-width: 100vw;
  padding-left: 15vw;
  padding-right: 15vw;
  // @media (min-width: $desktop) {
  //   max-width: $desktop-item-max-width;
  // }
}

h4 {
  color: $base-color;
}

// validations
.validation-warning {
  color: red;
}
.validation-warning-border {
  border: 1px solid red;
}

// paddings
.base-form-item {
  padding-top: 4px;
  padding-left: 20px;
  padding-bottom: 4px;
  padding-right: 20px;
  margin-top: 8px;
}
</style>
