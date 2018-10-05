<template>
  <div id="app">
    <Question></Question>
  </div>
</template>

<script>
import Question from './components/Question.vue'

export default {
  name: 'app',
  components: {
    Question
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
