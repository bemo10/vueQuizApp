
<script setup>
    import {defineProps, defineEmits} from "vue";

    const {question} = defineProps(["question"]);
    const emit = defineEmits(["selectedOption"]);

    const selectOption = (isCorrect) => {
        emit("selectedOption", isCorrect)
    }

</script>

<template>
    <div>
        <div class="question">
            <h1> Question: {{ question.text }}</h1>
        </div>
        <div class="options">
            <h1>Options:</h1>
            <div class="option" v-for="option in question.options" :key="index" @click="selectOption(option.isCorrect)">
                <h2>{{ option.label }}) {{ option.text }}</h2>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .option {
        cursor: pointer;
        background-color: rgb(236, 236, 236);
        margin-bottom: 20px;
    }
</style>