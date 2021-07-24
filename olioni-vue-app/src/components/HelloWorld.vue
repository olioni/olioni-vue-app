<template>
  <div id="main">
    <div id="topBox">
      <div class="questionWrap" v-for="(question, index) in qObj" :key="question">
        <div class="questionBox" v-if="index === qIndex"  :id="index"><strong> {{ question }} </strong></div>
      </div>
    </div>
    <div id="bottomBox">

      <div class="responseWrap" v-for="(reply, index) in qResponses" :key="index">
        <div class="responseContainer" v-if="index === qIndex" :id="index">
          <div class="response" :key="index" v-for="(items, index) in reply" :id="index" @click="highlightRespo(index, reply)">
            {{ items }}
          </div>
        </div>
      </div>

      <div class="submitWrap">
        <button class="submitButton" @click="nextQuestion()" v-if="submit">SUBMIT</button>
        <button class="submitButton" @click="displayEmailPopup()" v-if="finish">FINISH</button>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: [],
  data() {
    return {
      qObj: {q1: 'What happened?', q2: 'What did you want to happen? OR Think was going to happen?', q3: 'Who has been affected or hurt and how?', q4: 'What needs to happen to fix things up?', q5: 'Next time?'},
      questionArr: ['What happened?', 'What did you want to happen? OR Think was going to happen?', 'Who has been affected or hurt and how?', 'What needs to happen to fix things up?', 'What will you do next time?'],
      qResponses: {q1: ['Pushed', 'Hit', 'Kicked', 'Took Something', 'Bad/Nasty Words', 'Spat', 'Ignored', 'Upset Someone', 'Ran Away', 'Broke', 'Scratched', 'Made a Mess'], q2:['INSERT QUESTION 2 ARR']},
      qIndex: 'q1',

      selectedResponses: [],

      qInt: 1,

      buttonText: 'SUBMIT',
      submit: true,
      finish: false
    }
  },
  methods: {
    displayEmailPopup() {
      this.$emit('showPopup')
    },
    nextQuestion() {
      this.qInt++
      this.qIndex = 'q' + this.qInt

      if (this.qIndex == 'q5') {
        this.submit = false
        this.finish = true
      }

    },
    highlightRespo(id, reply) {
      document.getElementById(id).style = "background-color: #02d614; color: white;"
      this.selectedResponses.push(this.qResponses[this.qIndex][id])
      console.log(this.selectedResponses)
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
  height: 22vh;
  width: 100vw;

  display: flex;
  justify-content: center;
  align-items: center;
}

#bottomBox {
  height: 70vh;
  width: 100vw;

  display: flex;
  justify-content: center;
  align-items: center;
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

.responseWrap {
  display: flex;
  justify-content: center;
  align-items: center;
}

.responseContainer {
  width: 100%;
  display: flex;

  justify-content: center;
  align-items: center;

  flex-wrap: wrap;  
}

.response {
  background-color: white;
  
  width: 15vw;
  height: 25vh;

  border-radius: 10px;

  display: flex;
  justify-content: center;
  align-items: center;

  transition: 0.3s;

  margin-top: 4px;
  margin-right: 4px;
  margin-left: 4px;
  margin-bottom: 4px;
}

.response:hover{
  cursor: pointer;
  font-size: 18px;
}

.submitButton {
  width: 80vw;
  height: 10vh;
  
  background-color: white;

  border: none;
  border-radius: 10px;
  
  transition: 0.3s;
}

.submitButton:hover {
  cursor: pointer;
  font-size: 20px;

  background-color: rgb(238, 238, 238);
}
</style>
