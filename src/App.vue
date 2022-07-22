<script setup>
import QuestionJSON from "./questions.json";
import Workspace from "./components/Workspace.vue"
</script>

<template>
  <body v-if="QuestionJSON" class="app-wrapper">
    <header class="app-header">
      Quiz Application
    </header>
    <Workspace :questions="QuestionJSON.questions"/>
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
</style>
