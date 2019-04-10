<template>
  <div class="alert alert-success text-center">
    <h1>That's Correct!</h1>
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
