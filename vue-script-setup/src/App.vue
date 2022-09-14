<template>
<h1>Guess a number!</h1>
<h2>{{ message }}</h2>

<input v-model="userGuess">
<button @click = "compareGuess">Guess!</button>

</template>

<script setup>
import { ref } from 'vue'

let message = ref("");
let userGuess = ref("");
let randomNumber = ref(Math.floor(Math.random() * 10+1));

const compareGuess = () => {
  if(userGuess.value > 0 && userGuess.value <= 10) { 
    console.log(randomNumber);
    if(userGuess.value > randomNumber.value) {
      message.value = `${userGuess.value} is Too high! Try again!`;
    } else if(userGuess.value < randomNumber.value) {
      message.value = `${userGuess.value} is Too Low! Try again!`
    } else {
      message.value = `${userGuess.value} is correct! Congratulations!`
      randomNumber = Math.floor(Math.random()*10+1);
    }
  } else {
    message.value = `${userGuess.value} is invalid. Number must be between 1-10!`
  }
}

</script>



