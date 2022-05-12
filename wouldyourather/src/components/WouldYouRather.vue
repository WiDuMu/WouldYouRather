<template>
  <li class="wyr">
    <h3>{{ question }}</h3>
    <input type="radio" v-bind:value="answer1" v-model="choice" v-on:change="choiceMade"><label>{{answer1}}</label>
    <input type="radio" v-bind:value="answer2" v-model="choice" v-on:change="choiceMade"><label>{{answer2}}</label>
  </li>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: {
    id: Number,
    question: String,
    answer1: String,
    answer2: String
  },
  data() {
    return {
      choice: '',
    }
  },
  methods: {
    choiceMade() {
      this.$emit('answer-changed', {'id': this.id, 'choice': this.choice}) // I know there is a better way of keeping track of element than sending an ID, but I have very little mental energy atm
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input, label {
  border: 10px;
  border-color: red;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  opacity: 60%;
  margin: 0 10px;
  list-style: none;
}
a {
  color: #42b983;
}
</style>
