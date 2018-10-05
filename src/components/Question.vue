<template>
  <div class="container hello">
    <p class="question">What is <span class="bld">4 + 2</span>?</p>
    <div class="columns answers">
      <div class="column">
        <button class="button is-light is-large is-fullwidth">3</button>
      </div>
      <div class="column">
        <button class="button is-light is-large is-fullwidth">3</button>
      </div>
    </div>
    <div class="columns answers">
      <div class="column">
        <button class="button is-light is-large is-fullwidth">3</button>
      </div>
      <div class="column">
        <button class="button is-light is-large is-fullwidth">3</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {

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
