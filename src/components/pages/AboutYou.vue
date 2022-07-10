<template>
    <b-container class="mt-5">
        <h1>About You.</h1>
        <p>
            Information about you is used solely for anonymous statistics that
            help us understand our target audience. It is in no way attributed
            directly to you.
        </p>
        <div>
            <!--Age group -->
            <SingleSelect
                :question="items[0].question"
                :options="items[0].options"
                @singleSelectValueChanged="validateAge"
                :is-valid="isAgeValid"
            />
            <div v-if="!isAgeValid" class="validation-warning">
                {{ ageValidationMessage }}
            </div>
        </div>
        <div>
            <SingleSelect
                :question="items[1].question"
                :options="items[1].options"
            />
        </div>
    </b-container>
</template>

<script>
import SingleSelect from "../SingleSelect.vue";
// import MultiSelect from "../MultiSelect.vue";
import { items } from "../../assets/items.js";
export default {
    components: {
        SingleSelect,
        // MultiSelect,
    },
    data() {
        return {
            items: items,
            isAgeValid: true,
            ageValidationMessage:
                "Sorry, you must be at least 18 years old to participate in this survey.",
        };
    },
    methods: {
        validateAge(selected) {
            if (selected == "0-17") this.isAgeValid = false;
            else this.isAgeValid = true;
        },
    },
};
</script>

<style lang="scss" scoped></style>
