<template>
  <div id="app">
    <Question :valA="valA" :valB="valB"></Question>
  </div>
</template>

<script>
import Question from './components/Question.vue'

export default {
  name: 'app',
  components: {
    Question
  },
  data() {
    return {
      valA : 0,
      valB : 0,
      min: 1,
      max: 30,
    }
  },
  methods : {
    setRandomInt(){
      this.valA = Math.floor(Math.random() * (this.max - this.min + 1)) + this.min;
      this.valB = Math.floor(Math.random() * (this.max - this.min + 1)) + this.min;
    }
  },
  mounted() {
    this.setRandomInt()
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
