<template>
<section class="section">
  <div class="container box hello">
    <p class="question">What is <span class="bld">{{valA}} + {{valB}}</span>?</p>
    <div class="columns is-mobile answers">
      <div class="column">
        <button class="button is-light is-large is-fullwidth" @click="choosed(0)">{{options[0]}}</button>
      </div>
      <div class="column">
        <button class="button is-light is-large is-fullwidth" @click="choosed(1)">{{options[1]}}</button>
      </div>
    </div>
    <div class="columns is-mobile answers">
      <div class="column">
        <button class="button is-light is-large is-fullwidth" @click="choosed(2)">{{options[2]}}</button>
      </div>
      <div class="column">
        <button class="button is-light is-large is-fullwidth" @click="choosed(3)">{{options[3]}}</button>
      </div>
    </div>
  </div>
</section>
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
           } while(randomval == this.answer || this.options.slice(0,index+1).indexOf(parseInt(randomval)) != -1) //for each value to be unique
          this.$set(this.options, index, randomval);
          // this.options[index] = randomval  
        });
        // this.options[this.getRandomInt(0,3)]=this.answer;
        this.$set(this.options, this.getRandomInt(0,3), this.answer);
      },
      choosed(val) {
        if(this.options[val]==this.answer) {
          this.$emit("answered",{correct: true, answer : this.answer});
        } else {
          this.$emit("answered",{correct: false, answer : this.answer});
        }
      }
  },
  computed: {
    answer() {
      return this.valB+this.valA
    }
  },
  watch: {
    myvalA(newv,oldv) {
      this.changed()
    },
    myvalA(newv,oldv) {
      this.changed()
    },
    answer(newv,oldv) {
      this.changed()
    }
  },
  mounted() {
    this.changed()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  color: #636363;
  font-size: 28px;
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
/* .box {
  min-height: 350px;
} */
p {
    text-align: center;
    margin: 20px 0 30px!important;
    font-size: 1.25em;
}
</style>
