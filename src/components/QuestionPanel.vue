<script>
import AnswerRow from "./AnswerRow.vue";
export default {
  name: "QuestionPanel",
  components: { AnswerRow },
  props: {
    question: {
      type: Object,
      default: null,
    },
  },
};
</script>

<template>
  <div v-if="question" class="panel-wrapper">
    <AnswerRow v-for="answer of question.answers"/>
  </div>
</template>

<style scoped>
  .panel-wrapper{
    background-color: white;
    border-radius: 4px;
  }
</style>
