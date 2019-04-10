<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-8 col-sm-offset-2">
        <h1 class="text-center title">Math Quiz</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-sm-8 col-sm-offset-2">
        <transition name="flip" mode="out-in">
          <component
          class="card"
          :is="mode"
          @answered="checkAnswer($event)"
          @nextQuestion="mode = 'app-question'"></component>
        </transition>
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
    margin: 40px 0;
  }

  .flip-enter-active {
    animation: flip-in 0.5s ease-out forwards;
  }

  .flip-leave-active {
    animation: flip-out 0.5s ease-out forwards;
  }

  @keyframes flip-out {
    from {
      transform: rotateY(0deg);
    }
    to {
      transform: rotateY(90deg);
    }
  }

  @keyframes flip-in {
    from {
      transform: rotateY(90deg)
    }
    to {
      transform: rotateY(0deg)
    }
  }

</style>

