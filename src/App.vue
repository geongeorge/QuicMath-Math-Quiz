<template>
  <div id="app">
    <transition name="fade" mode="out-in">
      <h2 class="title is-h2" v-if="isstart">QuicMath</h2>
      <div v-else><h2 class="title is-h2">{{corrected}}/{{total}} <img class="restart" src="./assets/restart.png" @click="restartgame"></h2></div>
    </transition>
    <transition name="flip" mode="out-in">
       <Question :valA="valA" :valB="valB" @answered="answered" v-if="isquestion"></Question>
       <Result v-else @next="nextQuestion" :correct="iscorrect"></Result>
    </transition>

    
  </div>
</template>

<script>
import Question from './components/Question.vue'
import Result from "./components/Result.vue"

export default {
  name: 'app',
  components: {
    Question,
    Result
  },
  data() {
    return {
      valA : 0,
      valB : 0,
      min: 1,
      max: 30,
      isquestion : true,
      iscorrect : false,
      isstart : true,
      corrected : 0,
      total : 0,
    }
  },
  methods : {
    setRandomInt(){
      this.valA = Math.floor(Math.random() * (this.max - this.min + 1)) + this.min;
      this.valB = Math.floor(Math.random() * (this.max - this.min + 1)) + this.min;
    },
    answered(event){
      this.isstart = false;
      this.isquestion = false;
      // console.log(event["correct"] + " "+ event["answer"])

      this.iscorrect = event['correct']

      this.total++

      if(this.iscorrect==true) this.corrected++

      
      // this.isquestion = true;
    },
    nextQuestion() {
      this.isquestion=true
      this.setRandomInt()
    },
    restartgame() {
      this.total=0
      this.corrected=0
      this.isstart=true
      this.isquestion=true
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
.fade-enter-active, .fade-leave-active {
    transition: opacity .5s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0
}
/* .flip-enter {

} */
.flip-enter-active {
  animation: flip-in .3s ease-out forwards;
}
/* .flip-leave {

} */
.flip-leave-active {
  animation: flip-out .3s ease-in forwards;
}
@keyframes flip-out {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(-90deg);
  }
}
@keyframes flip-in {
  from {
    transform: rotateY(90deg);
  }
  to {
    transform: rotateY(0deg);
  }
}

.restart {
  /* position: fixed;
  top:50px;
  right:20px; */
  display: inline-block;
  vertical-align:middle;
  height: 40px;
  opacity: 0.2;
}
</style>
