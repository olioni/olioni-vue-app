<template>
  <emailPopup v-if="popup"/>
  <HelloWorld @showPopup="showPopup" />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import emailPopup from './components/emailPopup.vue'

export default {
  name: 'App',
  data() {
    return {
      popup: false,

      colorArr: ['#66b031', '#3162b0'],
      bgColor: ''
    }
  },
  components: {
    HelloWorld,
    emailPopup
  },
  methods: {
    showPopup() {
      this.popup = true

      let rng = Math.floor(Math.random() * this.colorArr.length)
      this.bgColor = this.colorArr[rng]
      this.colorArr.splice(rng, 1)
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
