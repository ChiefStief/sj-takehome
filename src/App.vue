<script setup>
import QuestionPanel from "./components/QuestionPanel.vue";
import QuestionJSON from './questions.json';
</script>

<template>
  <body v-if="QuestionJSON" class="app-wrapper">
    <header class="app-header">
      Quiz Application
    </header>
    <div class="workspace-wrapper">
<!--double check this css-->

      <h1>Quiz 1 - HTML / CSS / JS Practice</h1>
      <QuestionPanel v-for="question of QuestionJSON.questions" :id="question.id" :question="question" />
    </div>
  </body>
</template>

<style scoped>
  .app-wrapper{
    background-color: lightgray;
  }

  .app-header{
    background-color: #7C0200;
    color: white;
  }
  .workspace-wrapper{
    padding: 0 10px 0 10px;
  }
</style>
