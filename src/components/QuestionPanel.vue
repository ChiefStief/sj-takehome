<script>
export default {
  name: "QuestionPanel",
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
    isSubmissionAttempted: {
      type: Boolean,
      default: false,
    }
  },
  computed: {
    isCorrect () {
      return this.picked && this.isSubmitted && this.question.correctAnswerId === this.picked
    },
    isWrong () {
      return this.picked && this.isSubmitted && this.question.correctAnswerId !== this.picked
    },
    // feedbackColor () {
    //   if (isSubmissionAttempted && picked === null) {
    //     return 'yellow'
    //   }
    //   return this.isCorrect ? 'green' : 'red'
    // }
    // TODO: change color stuff to color to use feeback color
  }
};
</script>

<template>
  <div v-if="question" class="panel-wrapper" :class="{ 'inc-border': isSubmissionAttempted && picked === null, 'wrong-border': isWrong, 'correct-border': isCorrect }">
    <div>
      {{`${question.id}. ${question.text}`}}
    </div>
    <div class="answers-wrapper">
      <div v-for="answer of question.answers" class="a-row-wrapper" :class="{'correct-ans': isWrong && question.correctAnswerId === answer.id}">
        <div class="rad-btn">
          <input  type="radio" :id=answer.id :value=answer.id v-model="picked" @click="$emit('update-answers', {questionId:question.id, answerId:answer.id})" />
        </div>

          <label class="answer-text" :for="answer.id">{{answer.text}}</label>

      </div>
    </div>
    <div class="wrong-msg feedback-msg" v-if="isWrong">
      Wrong
    </div>
    <div class="correct-msg feedback-msg" v-if="isCorrect">
      Correct
    </div>
  </div>
</template>

<style scoped>
  .panel-wrapper{
    margin: 10px 0 10px 0;
    background-color: white;
    border-radius: 10px;
    padding: 20px;
    box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
  }

  .a-row-wrapper{
    padding: 7px 0 5px 7px;
    max-width: 75%;
    display: flex;
  }
  .answers-wrapper{
    padding-left: 15px;
  }
  .answer-text {
    padding-left: 10px;
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
  .wrong-msg{
    color: red;
  }

  .correct-msg{
    color: green;
  }
  .feedback-msg {
    position: absolute;
    bottom: 10px;
    right: 10px;
  }
  .correct-ans {
    background-color: green;
    border-radius: 10px;
    color: white;
    border: 2px solid darkgreen;
  }
  .rad-btn{
    align-self: flex-end;
  }
  @media (max-width: 1180px) {
    .answers-wrapper{
      padding-left: 0;
      margin-left: -7px;
    }
  }
</style>
