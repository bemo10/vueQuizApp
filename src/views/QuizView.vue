
<script setup>
    import {ref, computed} from "vue"
    import {useRoute, useRouter} from "vue-router";
    import quizes from "../data/quizes.json";
    import QuizHeader from "../components/QuizHeader.vue";
    import QuizQestions from "../components/QuizQuestion.vue"
    import QuizResult from "../components/QuizResullt.vue"

    const route = useRoute();
    const router = useRouter();
    const quizId = parseInt(route.params.id);
    const quiz = quizes.find(q => q.id === quizId);
    const questionIndex = ref(0);
    const correctAnswers = ref(0);

    const onOptionSelected = (isCorrect) => {
        questionIndex.value++;
        if (isCorrect) {
            correctAnswers.value++;
        }
    };

    const goHome = () => {
        router.push("/")
    };

</script>

<template>
    <div>
        <button @click="goHome">Home</button>
        <QuizHeader :name="quiz.name" :nQuestions="quiz.questions.length" :questionIndex="questionIndex"  />
        <QuizQestions v-if="questionIndex < quiz.questions.length" :question="quiz.questions[questionIndex]" @selectedOption="onOptionSelected" />
        <QuizResult v-else :nQuestions="quiz.questions.length" :correctAnswers="correctAnswers" />
    </div>
</template>

<style scoped>

</style>