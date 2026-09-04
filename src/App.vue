<script setup>
import { reactive } from "Vue";

const gameState = reactive({
  word: "",
  mistakes: 0,
  guessedLetters: [],
  gameLetters: [
    "a", "b", "c", "d", "e", "f", "g",
    "h", "i", "j", "k", "l", "m", "n",
    "o", "p", "q", "r", "s", "t", "u",
    "v", "w", "x", "y", "z",
    "ä", "ö", "ü", "ß"
  ]
})

async function startGame() {
  gameState.word = await getRandomWord();
}

startGame();
</script>

<template>
  <button v-for="letter in gameState.gameLetters" :key="letter" @click="guessLetter(letter)">
    {{ letter }}
  </button>
</template>