<template>
<section class="section">
    <div class="hello box">
        <div v-if="correct">
             <tick :correct="true"></tick>
        </div>
        <div v-else>
            <tick :correct="false"></tick>
        </div>
        <button class="button is-black" @click="$emit('next')">Next Question</button>
    </div>
</section>
</template>

<script>
import Tick from "./Tick.vue"
export default {
    components: {
        Tick
    },
    props: {
        correct : {default : false}
    }
}
</script>

<style scoped>
.hello {
  color: #2a2a2a;
  font-size: 35px;
  max-width: 400px;
  margin: 0 auto;
  margin-top: auto;
}
.box {
  min-height: 300px;
}
</style>
