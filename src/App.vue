<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-8 col-sm-offset-2">
        <h1 class="text-center title">Math Quiz</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-8 col-sm-offset-2">
        <component
          :is="mode"
          @answered="checkAnswer($event)"
          @nextQuestion="mode = 'app-question'"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Question from './components/Question';
import Answer from './components/Answer';

export default {
  data() {
    return {
      mode: 'app-question',
    };
  },
  components: {
    appQuestion: Question,
    appAnswer: Answer,
  },
  methods: {
    checkAnswer(isCorrect) {
      if (isCorrect) {
        this.mode = 'app-answer';
      } else {
        alert('Answer is incorrect'); // eslint-disable-line no-alert
      }
    },
  },
};
</script>

<style>
  .title {
    font-size: 26px;
  }
</style>

