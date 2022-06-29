<template>
  <div>
    <vue-slide-bar v-model="simpleValue" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      simpleValue: 50,
    };
  },
};
</script>

<style lang="scss" scoped></style>
