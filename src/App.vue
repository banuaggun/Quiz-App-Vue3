<template>
  <h1>Hello world</h1>
</template>

<script setup>
import {ref, computed} from 'vue'

const questions = ref([
  {
    question: 'What is VueJs?',
    answer:0,
    options:[
      'A Front End Framework',
      'A Library',
      'A Programming Language'
    ],
    selected: null
  },
  {
    question: 'What is ReactJs?',
    answer:2,
    options:[
      'A Front End Framework',
      'A Library',
      'A Programming Language'
    ],
    selected: null
  },
  {
    question: 'What is Vuex?',
    answer:1,
    options:[
      'A Front End Framework',
      'A State Management Library',
      'A Programming Language'
    ],
    selected: null
  }
])

const quizCompleted = ref(false);

const currentQuestion = ref(0);

const score = computed(() => {
  let value = 0;
  questions.value.map(q => {
    if(q.selected === q.answer){
      value++
    }
  })
  return value
})
</script>

<style>
  *{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  }
  body{
    background-color:#f2f2f2;
    color:#212121;
  }
</style>
