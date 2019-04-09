<template>
  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 class="panel-title text-center">{{ question }}</h3>
    </div>
    <div class="panel-body">
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg">{{ buttonData[0].answer}}</button>
      </div>
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg">{{ buttonData[1].answer}}</button>
      </div>
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg">{{ buttonData[2].answer}}</button>
      </div>
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg">{{ buttonData[3].answer}}</button>
      </div>
    </div>
  </div>
</template>

<script>
const MODE_ADDITION = 1;
const MODE_SUBTRACTION = 2;
const MODE_MULTIPLICATION = 3;
const MODE_DIVISION = 4;

export default {
  data() {
    return {
      question: 'Ooops...something goes wrong',
      buttonData: [
        { correct: false, answer: 0 },
        { correct: false, answer: 0 },
        { correct: false, answer: 0 },
        { correct: false, answer: 0 },
      ],
    };
  },
  methods: {
    createQuestion() {
      let correctNumber;
      const firstNumber = this.getRandomNumber(1, 100);
      const secondNumber = this.getRandomNumber(1, 100);
      const thirdNumber = this.getRandomNumber(1, 10);
      const fourthNumber = this.getRandomNumber(1, 10);
      const mode = this.getRandomNumber(1, 4);

      switch (mode) {
        case MODE_ADDITION:
          correctNumber = firstNumber + secondNumber;
          this.question = `What's ${firstNumber} + ${secondNumber}?`;
          break;
        case MODE_SUBTRACTION:
          correctNumber = firstNumber - secondNumber;
          this.question = `What's ${firstNumber} - ${secondNumber}?`;
          break;
        case MODE_MULTIPLICATION:
          correctNumber = thirdNumber * fourthNumber;
          this.question = `What's ${thirdNumber} * ${fourthNumber}?`;
          break;
        case MODE_DIVISION:
          correctNumber = thirdNumber;
          this.question = `What's ${thirdNumber * fourthNumber} / ${fourthNumber}?`;
          break;
        default:
          correctNumber = 0;
          this.question = 'Ooops...something goes wrong';
      }

      this.createOptions(correctNumber);
    },
    createOptions(correctNumber) {
      this.buttonData[0].answer = this.getRandomNumber(correctNumber - 10,
        correctNumber + 10, correctNumber);
      this.buttonData[0].correct = false;
      this.buttonData[1].answer = this.getRandomNumber(correctNumber - 10,
        correctNumber + 10, correctNumber);
      this.buttonData[1].correct = false;
      this.buttonData[2].answer = this.getRandomNumber(correctNumber - 10,
        correctNumber + 10, correctNumber);
      this.buttonData[2].correct = false;
      this.buttonData[3].answer = this.getRandomNumber(correctNumber - 10,
        correctNumber + 10, correctNumber);
      this.buttonData[3].correct = false;

      const correctOption = this.getRandomNumber(0, 3);
      this.buttonData[correctOption].answer = correctNumber;
      this.buttonData[correctOption].correct = true;
    },
    getRandomNumber(min, max, except) {
      const randomNumber = Math.round(Math.random() * (max - min)) + min;

      if (randomNumber === except) {
        return this.getRandomNumber(min, max, except);
      }

      return randomNumber;
    },
  },
  created() {
    this.createQuestion();
  },
};
</script>

<style scoped>
  .btn {
    margin: 10px;
  }
</style>

