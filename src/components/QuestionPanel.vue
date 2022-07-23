<script>
// import AnswerRow from "./AnswerRow.vue";
export default {
  name: "QuestionPanel",
  // components: { AnswerRow },
  data () {
    return {
      picked: null,
    }
  },
  props: {
    question: {
      type: Object,
      default: null,
    },
    isSubmitted: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<template>
  <div v-if="question" class="panel-wrapper" :class="{ 'inc-border': isSubmitted && picked === null, 'wrong-border': isSubmitted && picked && question.correctAnswerId !== picked, 'correct-border': isSubmitted && question.correctAnswerId === picked }">
    {{isSubmitted}}
    {{picked}}
    {{question.correctAnswerId}}
    <div>
      {{`${question.id}. ${question.text}`}}
    </div>
    <div v-for="answer of question.answers" class="a-row-wrapper">
      <input type="radio" :id=answer.id :value=answer.id v-model="picked" @click="$emit('update-answers', {questionId:question.id, answerId:answer.id})" />
      <label class="answer-text" :for="answer.id">{{answer.text}}</label>
    </div>
<!--    <AnswerRow v-for="answer of question.answers" :answer="answer"/>-->
  </div>
</template>

<style scoped>
  .panel-wrapper{
    margin: 10px 0 10px 0;
    background-color: white;
    border-radius: 10px;
    padding: 10px;
    /*box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;*/
    box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
  }
  .a-row-wrapper{
    padding: 5px 0 5px 15px;
  }
  .answer-text {
    padding-left: 5px;
  }
  .inc-border{
    border: 2px solid yellow;
  }

  .wrong-border{
    border: 2px solid red;
  }

  .correct-border{
    border: 2px solid green;
  }
</style>
