<template>
  <emailPopup v-if="popup" :responsesObj="responsesObj"/>
  <surveyPopup @showPopup="showPopup" v-if="start" @responses="pushObj"/>
  <startPopup v-if="open" @showApp="showApp"/>
</template>

<script>
import surveyPopup from './components/surveyPopup.vue'
import emailPopup from './components/emailPopup.vue'
import startPopup from './components/startPopup.vue'

export default {
  name: 'App',
  props: ['responses'],
  data() {
    return {
      popup: false,
      start: false,
      open: true,

      responsesObj: {}
    }
  },
  components: {
    surveyPopup,
    emailPopup,
    startPopup
  },
  methods: {
    showPopup() {
      this.popup = true
      this.start = false
      // console.log(responses)
    },
    showApp() {
      this.open = false
      this.start = true
    },
    pushObj(e) {
      console.log(e)
      this.responsesObj = e
    }
  }
}
</script>

<style>
* {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
