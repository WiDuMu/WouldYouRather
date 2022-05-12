<template>
  <div class="app">
    <h1>Would you rather... </h1>
    <h2>Please make your choice!</h2>
    <ul>
    <would-you-rather v-for="question in questions" v-bind:key="question.id" v-bind:id="question.id" v-bind:question="question.question" 
    v-bind:answer1="question.answer1" 
    v-bind:answer2="question.answer2"
    v-on:answer-changed="answerChanged"></would-you-rather></ul>
    <div v-show="questions.some(question => {return (question.selection)})">
    <h2>You chose:</h2>
    <ul>
      <li v-for="question in questions" v-bind:key="question.id">{{ question.selection }}</li>
    </ul>
    </div>
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
      questions: [
        {
          id: 0,
          question: 'take a coding class or an art class?',
          answer1: 'Coding all the way!',
          answer2: "I prefer to be 'creative'.",
          selection: '' //where the user's input is stored
        },
        {
          id: 1,
          question: 'Would you rather live on the beach or in a cabin in the woods?',
          answer1: 'Idyllic beach',
          answer2: "Woods all the way",
          selection: ''
        },
        {
          id: 2,
          question: 'Would you rather run at 100 mph or fly at 20 mph?',
          answer1: 'Running champion here I come!',
          answer2: "I can FLY!",
          selection: ''
        },
      ],
    }
  },
  methods: {
    answerChanged(event) {
      console.log(event)
      this.questions[event.id].selection = event.choice; //this line takes the event from the input and stores the relevant choice in the answers selection.
    }
  }
}
</script>

<style>
h1 {
  margin: 0px;
  padding-top: 10px;
}
#app {
  margin: 0px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: blueviolet;
  height: 100%;
  width: 100%;
  /*I seek to provide the worst UI ever */
}
</style>
