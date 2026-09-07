<script setup>
import { reactive, ref } from "vue";
import Word from "./components/Word.vue";

const letterInput = ref("");

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

function guessLetter(guessedLetter) {
  if (guessedLetter === "") {
    return;
  }

  if (!gameState.gameLetters.includes(guessedLetter)) {
    alert("Bitte einen Buchstaben eingeben");
    return;
  }

  if (!gameState.guessedLetters.includes(guessedLetter)) {
    gameState.guessedLetters.push(guessedLetter);

    if (!gameState.word.includes(guessedLetter)) {
      gameState.mistakes++;
    }
  }
}

function submitGuess() {
  guessLetter(letterInput.value.toLowerCase());
  letterInput.value = "";
}

</script>

<template>

  <Word :word="gameState.word" :guessedLetters="gameState.guessedLetters" />

  <input v-model="letterInput" maxlength="1" @keydown.enter="submitGuess">

  <br>

  <button @click="submitGuess">
    Raten
  </button>

  <button v-for="letter in gameState.gameLetters" :key="letter" @click="guessLetter(letter)">
    {{ letter }}
  </button>
</template>