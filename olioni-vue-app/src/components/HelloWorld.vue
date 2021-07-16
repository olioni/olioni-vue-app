<template>
  <div id="main">
    <div id="topBox">
      <div class="questionWrap" v-for="(question, index) in questionsObj" :key="question">
        <div class="questionBox" v-if="index === questionIndex"  :id="index"> {{ question }} </div>
      </div>
    </div>
    <div id="bottomBox">

      <div class="checkBoxDiv" :key="question" v-for="(response, question) in responses">
        <div class="checkBox" @click="setSelected()" v-for="questionReplys in reponse" :key="questionReplys">
          <h3 class="checkBoxText"> {{ questionReplys }}</h3>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import {questionsObj} from '@/components/data.js'
import {questions} from '@/components/data.js'
import {responses} from '@/components/data.js'

export default {
  name: 'HelloWorld',
  props: [],
  data() {
    return {
      questionsObj: questionsObj,
      questions: questions,
      responses: responses,

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

  display: flex;
  justify-content: center;
  /* align-items: center; */
  flex-direction: row;
  flex-wrap: wrap;
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

.checkBoxDiv {
  width: 12vw;
  height: 12vh;

  display: flex;
  justify-content: center;
  align-items: center;
}

.checkBox {
  background-color: white;
  
  color: black;

  width: 10vw;
  height: 10vh;

  border-radius: 15px;

  display: flex;
  justify-content: center;
  align-items: center;

  transition: 0.3s;
}

.checkBox:hover {
  cursor: pointer;
}

.checkBoxText {
  color: black;
}
</style>
