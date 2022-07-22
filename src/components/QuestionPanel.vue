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
  },
};
</script>

<template>
  <div v-if="question" class="panel-wrapper">
    <div>
      {{`${question.id}. ${question.text}`}}
    </div>
    <div v-for="answer of question.answers" class="a-row-wrapper">
      <input type="radio" :id=answer.id :value=answer.id v-model="picked" @click="$emit('update-answers', {questionId:question.id, answerId:answer.id})" />
      <label :for="answer.id">{{answer.text}}</label>
    </div>
<!--    <AnswerRow v-for="answer of question.answers" :answer="answer"/>-->
  </div>
</template>

<style scoped>
  .panel-wrapper{
    margin: 8px 0 8px 0;
    background-color: white;
    border-radius: 10px;
    padding: 10px;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  }
  .a-row-wrapper{
    padding: 5px 0 5px 15px
  }
</style>
