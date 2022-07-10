<template>
    <div>
        <ProgressBar />
        <div id="app">
            <AboutYou />
            <AboutYou />
            <AboutYou />
            <AboutYou />
            <div class="form-controls">
                <b-button class="m-3">SUBMIT</b-button>
            </div>
        </div>
    </div>
</template>

<script>
import AboutYou from "./components/pages/AboutYou.vue";
import ProgressBar from "./components/ProgressBar.vue";
export default {
    name: "App",
    components: { AboutYou, ProgressBar },
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

.progress {
    opacity: 1;
    border-radius: 0 !important;
    height: 40px !important;
    .progress-bar {
        background-color: $base-color;
        border-radius: 0 !important;
    }
}

.form-controls {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    button {
        width: 100%;
        background-color: $base-color;
        color: white;
        border: none;
    }
}
</style>
