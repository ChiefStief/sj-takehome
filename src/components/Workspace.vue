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
      isSubmitted: false
    }
  },
  computed: {
    areUnanswered() {
      return Object.entries(this.answers).length < this.questions.length
    },
    numRight() {
      return this.questions.filter(question=>{
        return question.correctAnswerId === this.answers[question.id]
      }).length
    },
    percentRight() {
      return Math.round(this.numRight*100/this.questions.length)
    }
  },
  methods: {
    updateAnswers({questionId, answerId}) {
      this.answers[questionId] = answerId
    },
    onSubmit() {
      this.isSubmitted = true
    }
  },
}
</script>

<template>
  <div class="workspace-wrapper">
    <!--double check this css-->
    <h1>Quiz 1 - HTML / CSS / JS Practice</h1>
    <div v-if="isSubmitted" class="results-wrapper">
      <div class="results-title">Results</div>
      <div class="results-text">You got {{numRight}}/{{questions.length}}</div>
      <div class="results-percent">{{percentRight}}%</div>
    </div>
    <QuestionPanel v-for="question of questions" :is-submitted="isSubmitted" :question="question" :answer-given="answers[question.id] || null" @update-answers="updateAnswers"/>
    <div class="submission-blk">
      <button type="button" class="submit-btn" @click="onSubmit">Submit</button>
      <div v-if="areUnanswered" class="unanswered-block">Answer all questions before submitting. Unanswered questions are displayed in yellow.</div>
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
.results-title{
  text-decoration: underline;
}

.results-percent{
  color: red;
  font-weight: bolder;
}

.results-wrapper{
  text-align: center;
}
</style>
