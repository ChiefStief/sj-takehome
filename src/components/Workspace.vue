<script>
import QuestionPanel from "./QuestionPanel.vue";

export default {
  name: "Workspace",
  components: { QuestionPanel },
  props: {
    questions: {
      type: Array,
      default: () => [],
    },
  },
  data () {
    return {
      answers: { },
    }
  },
  computed: {
    isUnanswered () {
      return Object.entries(this.answers).length < this.questions.length
    },
  },
  methods: {
    updateAnswers ({questionId, answerId}) {
      this.answers[questionId] = answerId
    },
  },
}
</script>

<template>
  <div class="workspace-wrapper">
    <!--double check this css-->
    <h1>Quiz 1 - HTML / CSS / JS Practice</h1>
    {{answers}}
    <QuestionPanel v-for="question of questions" :question="question" @update-answers="updateAnswers"/>
    <div class="submission-blk">
      <button type="button" class="submit-btn">Submit</button>
      <div v-if="isUnanswered" class="unanswered-block">Answer all questions before submitting. Unanswered questions are displayed in yellow.</div>
    </div>
  </div>

</template>

<style scoped>
.workspace-wrapper{
  padding: 0 10px 30px 10px;
}
.submit-btn{
  background-color: green;
  border-radius: 4px;
  color: white;
  padding: 10px;
}
.submission-blk{
  text-align: center;
}
.unanswered-block{
  text-align: center;
  color: red;
  padding-top: 10px;
}
</style>
