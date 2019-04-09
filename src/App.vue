<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-8 col-sm-offset-2">
        <h1 class="text-center title">Math Quiz</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-8 col-sm-offset-2">
        <component :is="mode"></component>
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
};
</script>

<style>
  .title {
    font-size: 26px;
  }
</style>

