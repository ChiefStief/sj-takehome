<script setup>
import QuestionPanel from "./components/QuestionPanel.vue";
import QuestionJSON from './questions.json';
</script>

<template>
  <div class="app-wrapper">
<!--double check this css-->
    <header class="app-header">
      Quiz Application
    </header>
    <h1>Quiz 1 - HTML / CSS / JS Practice</h1>
    <QuestionPanel v-for="question of QuestionJSON.questions" :id="question.id" :question="question" />
  </div>
</template>

<style scoped>
  .app-wrapper{
    background-color: lightgray;
  }

  .app-header{
    background-color: #7C0200;
    color: white;
  }
</style>
