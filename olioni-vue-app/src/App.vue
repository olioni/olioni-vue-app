<template>
  <emailPopup v-if="popup"/>
  <HelloWorld @showPopup="showPopup" v-if="start" />
  <startPopup v-if="open" @showApp="showApp"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import emailPopup from './components/emailPopup.vue'
import startPopup from './components/startPopup.vue'

export default {
  name: 'App',
  data() {
    return {
      popup: false,
      start: false,
      open: true
    }
  },
  components: {
    HelloWorld,
    emailPopup,
    startPopup
  },
  methods: {
    showPopup() {
      this.popup = true
      this.start = false
    },
    showApp() {
      this.open = false
      this.start = true
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
