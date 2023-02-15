<template>
  <main class="app">
    <h1>Quiz</h1>
    <section class="quiz">
      <div class="quiz-info">
        <span class="quiz-questions">
          {{ getCurentQuestion.question }}
        </span>
        <span class="quiz-score">
          Score {{ score }} / {{ questions.length }}
        </span>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, computed } from "vue";

const questions = ref([
  {
    question: "What is VueJs?",
    answer: 0,
    options: ["A Front End Framework", "A Library", "A Programming Language"],
    selected: null,
  },
  {
    question: "What is ReactJs?",
    answer: 2,
    options: ["A Front End Framework", "A Library", "A Programming Language"],
    selected: null,
  },
  {
    question: "What is Vuex?",
    answer: 1,
    options: [
      "A Front End Framework",
      "A State Management Library",
      "A Programming Language",
    ],
    selected: null,
  },
]);

const quizCompleted = ref(false);

const currentQuestion = ref(0);

const score = computed(() => {
  let value = 0;
  questions.value.map((q) => {
    if (q.selected === q.answer) {
      value++;
    }
  });
  return value;
});

const getCurentQuestion = computed(() => {
  let question = questions.value[currentQuestion.value];
  question.index = currentQuestion.value;
  return question;
});

const SetAnswer = (evt) => {
  questions.value[currentQuestion.value].selected = evt.target.value;
  evt.target.value = null;
};

const NextQuestion = () => {
  if (currentQuestion.value < questions.value.length - 1) {
    currentQuestion.value++;
  } else {
    quizCompleted.value = true;
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
}
body {
  background-color: #f2f2f2;
  color: #212121;
}
</style>
