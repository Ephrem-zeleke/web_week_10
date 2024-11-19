<script setup>
import WouldYouRather from './components/WouldYouRather.vue'
//we need to import the ref library and store the question and answer for the user

import { ref } from 'vue'
const wyrQuestion = ref('Live in a house shaped like a triangle or a house shaped like circle')
const wyrAnswer1 = ref('Triangle house ')
const wyrAnswer2 = ref('Circle house ')

// we also need a variable that response the user response

const userSelection = ref('') // we don't know the user selection so we left it empty
// now we have to send the question and answer to the would you rather to display and we use v-bind
function updateUserSelection (userChoice) {
  userSelection.value = `Thank you, you choose ${userChoice}`
}

</script>

<template>
<div id="app-component">

  <h1>would you rather?</h1>

  <WouldYouRather v-bind:question="wyrQuestion"
  v-bind:answer1="wyrAnswer1"
  v-bind:answer2="wyrAnswer2"
  v-on:answer-selected="updateUserSelection">
  </WouldYouRather>

  <p>{{ userSelection }}</p>
<!--  the parent will receive the child message and it will display
to do that, we will use the v-on and create a function to display the message -->
<!--this will be replaced by would you rather template -->

</div>
</template>

<style scoped>
#app-component {
  background-color: #e4a5bd;
}

</style>
