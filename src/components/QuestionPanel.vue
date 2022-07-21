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
      <input type="radio" :id=answer.id :value=answer.id v-model="picked" />
      <label :for="id">{{answer.text}}</label>
    </div>
<!--    <AnswerRow v-for="answer of question.answers" :answer="answer"/>-->
  </div>
</template>

<style scoped>
  .panel-wrapper{
    margin: 5px 0 5px 0;
    background-color: white;
    border-radius: 4px;
  }
  .a-row-wrapper{
    padding: 5px 0 5px 15px
  }
</style>
