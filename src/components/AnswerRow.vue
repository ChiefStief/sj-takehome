<script>
export default {
  name: "QuestionRow",
  props: {
    answer: {
      type: Object,
      default: null,
    },
  },
};
</script>

<template>
  <div v-if="answer" class="a-row-wrapper">
    <input type="radio" :id=answer.id v-model="picked" />
    <label for=id>{{answer.text}}</label>
  </div>
</template>

<style scoped>
  .q-row-wrapper{

  }
</style>
