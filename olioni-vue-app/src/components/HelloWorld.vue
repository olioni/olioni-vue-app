<template>
  <div id="main" :style="{backgroundColor: bgClr}">
    <div id="topBox">
      <div class="questionWrap" v-for="(question, index) in qObj" :key="question">
        <div class="questionBox" v-if="index === qIndex"  :id="index"><strong> {{ question.toUpperCase() }} </strong></div>
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
        <button class="submitButton" @click="nextQuestion(), changeBgColor()" v-if="submit">NEXT</button>
        <button class="submitButton" @click="displayEmailPopup()" v-if="finish">SUBMIT</button>
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
      qObj: {q1: 'What happened?', q2: 'What did you want to happen? OR Think was going to happen?', q3: 'Who has been affected or hurt?', q4: 'How?', q5: 'What needs to happen to fix things up?', q6: 'Next time?'},
      qResponses: {q1: ['Pushed', 'Hit', 'Kicked', 'Took Something', 'Bad/Nasty Words', 'Spat', 'Ignored', 'Upset Someone', 'Ran Away', 'Broke', 'Scratched', 'Made a Mess'], q2:['Angry', 'Go Away', 'Frustrated', "Don't Like/Don't Want To", 'Confused', 'Want To Play', 'Worried', 'Want To Go Home', 'Stop', 'Need Help', 'Not Fair'], q3: ['Student/Child', 'Teacher', 'School Helper', 'Teacher Aide', 'Whole Class', 'Grandparents', 'Bus Driver', 'Mum/Dad', 'Principal/DP'], q4: ['Hurt Head/Face', 'Hurt Arm', 'Hurt Leg', 'Broke Something', 'Made a Mess', 'Hurt Ears', 'Made Someone Scared', 'Made Someone Cry', 'Made Someone Embarassed', 'Made Someone Worried', "Hurt Someone's Feelings", 'Made Someone Sad'], q5: ['Give/Give Back', 'Say Something Nice', 'Check If Ok', 'Fix', 'Offer To', 'Help', 'Clean Up', 'Say I Will',]},
      qIndex: 'q1',
      qEmoji: {q1: ['✋', '🤛', '🦵', '🐱‍👤', '🤬', '💧', '🤐', '😡', '🏃‍♂️', '👋', '']},
      selectedResponses: [],

      qInt: 1,

      buttonText: 'NEXT',
      submit: true,
      finish: false,

      colorArr: ['#8f02e0', '#e0025f', '#37db81', '#e37100', '#ad0c0c'],
      bgClr: '#1e6ae3'
    }
  },
  methods: {
    changeBgColor() {
      let rng = Math.floor(Math.random() * this.colorArr.length)
      this.bgClr = this.colorArr[rng]
      this.colorArr.splice(rng, 1)
    },
    displayEmailPopup() {
      this.$emit('showPopup')
    },
    nextQuestion() {
      this.qInt++
      this.qIndex = 'q' + this.qInt

      if (this.qIndex != 'q4') {
        this.buttonText = 'NEXT'
      } else {
        this.buttonText = 'SUBMIT'
      }

      if (this.qIndex == 'q5') {
        this.submit = false
        this.finish = true
      }

    },
    highlightRespo(id, reply) {
      document.getElementById(id).style = "background-color: #02d614; color: white;"
      this.selectedResponses.push(this.qResponses[this.qIndex][id])
      console.log(this.selectedResponses)
    },
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

  transition: 0.6s;
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

  font-size: 18px;
  color: black;
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

  flex-wrap: wrap;
  text-overflow: hidden;

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

@media only screen and (max-width: 600px) {
  .response {
    height: 16vh;
    width: 20vw;
    font-size: 17px;
  }

  .responseWrap {
    height: 60vh;
  }

  .responseContainer {
    height: 51vh;
    width: 90vw;
    display: flex;
  }

  .questionBox {
    width: 80vw;
    font-size: 30px;
  }

  .submitButton {
    height: 10vh;
    font-size: 30px;
  }

}
</style>
