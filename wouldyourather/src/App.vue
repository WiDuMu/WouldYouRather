<template>
  <div class="app">
    <h1>Would you rather... </h1>
    <would-you-rather v-bind:question="wyrQuestion" 
    v-bind:answer1="wyrAnswer1" 
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"></would-you-rather>

    <p>{{userSelectionMessage}}</p>
  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: 'Would you rather take a coding class or an art class?',
      wyrAnswer1: 'Coding all the way!',
      wyrAnswer2: "I prefer to be 'creative'.",
      userSelectionMessage: ''
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks, you chose ${choice}`
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: blueviolet;
  /*I seek to provide the worst UI ever */
}
</style>
