<template>
  <div class="container hello">
    <p class="question">What is <span class="bld">{{valA}} + {{valB}}</span>?</p>
    <div class="columns answers">
      <div class="column">
        <button class="button is-light is-large is-fullwidth">{{options[0]}}</button>
      </div>
      <div class="column">
        <button class="button is-light is-large is-fullwidth">{{options[1]}}</button>
      </div>
    </div>
    <div class="columns answers">
      <div class="column">
        <button class="button is-light is-large is-fullwidth">{{options[2]}}</button>
      </div>
      <div class="column">
        <button class="button is-light is-large is-fullwidth">{{options[3]}}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    valA: {default: 0},
    valB: {default: 0},
  },
  data() {
    return {
      options: [0,0,0,0]
    }
  },
  methods: {
      getRandomInt(min, max) {
          return Math.floor(Math.random() * (max - min + 1)) + min;
      },
      changed() { 
        this.options.forEach((item, index, arr)=>{
          let randomval = 0;
           do {
            randomval = this.getRandomInt(this.answer-5,this.answer+5)
           } while(this.options.slice(0,index+1).indexOf(parseInt(randomval)) != -1) //for each value to be unique
          arr[index] = randomval          
        });

        this.options[this.getRandomInt(0,3)]=this.answer;
      }
  },
  computed: {
    answer() {
      return this.valB+this.valA
    }
  },
  watch: {
    valA(newv,oldv) {
      this.changed()
    },
    valB(newv,oldv) {
      this.changed()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  color: #636363;
  font-size: 40px;
  max-width: 400px;
  margin: 0 auto;
}
.hello .bld{
  color: #323232;
  font-weight: bold;
}
.answers {
  margin: 10px auto;
  font-weight: bold;
  color: #636363;
}
.answers:hover {
  color: #323232;
}
.answers .columnn{
  padding-left: 10px;
  padding-right: 10px;
}
</style>
