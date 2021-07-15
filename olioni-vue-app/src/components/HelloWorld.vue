<template>
  <div id="main">
    <div id="topBox">
      <div class="questionWrap" v-for="(question, index) in questionsObj" :key="question">
        <div class="questionBox" v-if="index === questionIndex"  :id="index"> {{ question }} </div>
      </div>
    </div>
    <div id="bottomBox">

      <div id="testButtons">
        <button @click="decreaseIndex()"><h3>Decrease</h3></button>
        <button @click="increaseIndex()"><h3>Increase</h3></button>
      </div>

    </div>
  </div>
</template>

<script>
import {questionsObj} from '@/components/data.js'
import {questions} from '@/components/data.js'

export default {
  name: 'HelloWorld',
  props: [],
  data() {
    return {
      questionsObj: questionsObj,
      questions: questions,
      questionIndex: 'question1',
      index: 0
    }
  },
  methods: {
    increaseIndex() {
      this.index++
      this.questionIndex = this.questions[this.index]
    },
    decreaseIndex() {
      this.index--
      this.questionIndex = this.questions[this.index]
    }
  },
  mounted() {
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
}

#main {
  background-color: #1e6ae3;
  
  display: flex;
  width: 100vw;
  height: 100vh;

  justify-content: center;
  align-items: center;

  flex-direction: column;
}

#topBox {
  height: 25vh;
  width: 100vw;

  display: flex;
  justify-content: center;
  align-items: center;
}

#bottomBox {
  height: 75vh;
  width: 100vw;
}

h3 {
  color: white;
}

.questionWrap {
  display: flex;
  
  justify-content: center;
  align-items: center;
  
}

.questionBox {
  height: 20vh;
  width: 40vw;

  background-color: white;

  display: flex;
  justify-content: center;
  align-items: center;

  border-radius: 15px;
}
</style>
