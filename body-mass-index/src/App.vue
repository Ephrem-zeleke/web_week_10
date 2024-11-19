<script setup>
import BodyMassIndexForm from './components/BodyMassIndexForm.vue'

import { ref } from 'vue'
// here in the script, let us set the bmi first to 0
const bmi = ref(0)

// we will create a function that handle the data from the child and do the maths
// this function also display the result
const handleStatEntered = ({height, weight})=>{
  if (height > 0 && weight > 0) {
    bmi.value = weight/(height*height)
  }else {
    alert('Please enter a valid value for height and weight')
  }
  return {bmi, handleStatEntered}
}

</script>

<template id="app-components">



  <div class="app">
    <h1>Body mass index calculator</h1>
<!--we will call a function and setup the expected message -->
    <BodyMassIndexForm @stats-entered="handleStatEntered"/>

    <div v-if="bmi !== null" class="bmi-result">
      <p>Your BMI is : <strong>{{ bmi.toFixed(2) }}</strong></p>
    </div>

  </div>

</template>

<style scoped>
.app {
  border: 3px solid #99b2e6;
  padding: 20px;
  border-radius: 8px;
  max-width: 500px;
  margin: auto;
  text-align: center;
  background-color: #f9f9f9;
}
</style>
