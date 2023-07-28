
<script setup>
    import {defineProps} from "vue";

    const {name, nQuestions, questionIndex} = defineProps(["name", "nQuestions", "questionIndex"]);


</script>

<template>
    <div>
        <h1>Quiz: {{ name }}</h1>
        <h2 v-if="questionIndex < nQuestions">Question {{ questionIndex + 1 }} / {{ nQuestions }}</h2>
    </div>
</template>

