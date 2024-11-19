<script setup>
import { ref } from 'vue'

defineProps({
})
// these are the value that the user entered
const height = ref(0)
const weight = ref(0)
// when the user click the calculate button, the child will emit an event called stats-entered to the parent
const emit = defineEmits([
      'stats-entered'])

// here we will create a function that return  the user height and weight data

const calculateBMI = () =>{
  emit('stats-entered', {height:height.value, weight:weight.value})
  // clear the input after emitting the data
  height.value = null;
  weight.value = null;
  return height, weight, calculateBMI
}
</script>

<template>
  <div id="bmi-form">
    <h2>Enter your height and weight</h2>

    <div>
      <label for="user-height">Height in meter</label>
      <input v-model="height" id="user-height" type="number">
    </div>

    <div>
      <label for="user-weight">Weight in kilogram</label>
      <input v-model="weight" id="user-weight" type="number">
    </div>
    <br>

    <div>
<!--      add an event when the calculate button clicked and we use the v-on, it will send the data to the parent app-->
      <button v-on:click="calculateBMI">Calculate</button>
    </div>


  </div>

</template>

<style scoped>
#bmi-form {
  border: 3px solid red;
  padding: 15px;
  border-radius: 8px;
  max-width: 300px;
  margin: auto;
  background-color: #fff8f8;
}
button {
  background-color: #04AA6D; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>
