<template>
    <div id="progress-bar">
        <b-progress :value="progress" />
    </div>
</template>

<script>
export default {
    props: {
        progress: {
            type: Number,
            default: 4,
        },
    },
};
</script>

<style lang="scss" scoped>
@import "../definitions.scss";
.navbar {
    background-color: $base-color;
    z-index: -1;
}

#progress-bar {
    position: sticky;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
</style>
