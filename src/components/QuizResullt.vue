<script setup>
    import {defineProps} from "vue";

    const {nQuestions, correctAnswers} = defineProps(["nQuestions", "correctAnswers"]);
    const result = Math.round((correctAnswers / nQuestions) * 100 * 10) / 10;
</script>

<template>
    <div>
        <h1>Result:</h1>
        <h2>{{ correctAnswers }} / {{ nQuestions }} ({{ result }}%) correct</h2>
    </div>
</template>
