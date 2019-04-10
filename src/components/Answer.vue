<template>
  <div class="alert alert-success text-center">
    <h3 class="title--big">That's Correct!</h3>
    <hr>
    <button class="btn btn-primary" @click="showNextQuestion">Next Question</button>
  </div>
</template>

<script>
export default {
  methods: {
    showNextQuestion() {
      this.$emit('nextQuestion');
    },
  },
};
</script>

<style scoped>
  .alert {
    padding: 40px 0;
  }

  .btn {
    margin-top: 30px;
    padding: 10px 20px;
  }

  .title--big {
    font-size: 30px;
  }
</style>
