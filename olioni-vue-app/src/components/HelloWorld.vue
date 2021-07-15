<template>
  <div id="main">
    <div id="topBox"></div>
    <div id="bottomBox"></div>
  </div>
</template>

<script>
import { questions } from 'components/data.js'

export default {
  name: 'HelloWorld',
  props: [],
  data() {
    return {
      questionIndex: '',
      question: question
    }
  },
  methods: {

  },
  mounted() {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#main {
  background-color: #1e6ae3;
  
  display: flex;
  width: 100vw;
  height: 100vh;

  justify-content: center;
  align-items: center;
}

h3 {
  color: white;
  font-size: 100px;
}
</style>
