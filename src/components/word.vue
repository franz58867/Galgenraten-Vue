<script setup>
import { computed } from "Vue";
defineProps(["word", "guessedLetters"]);
</script>
<template>
    <p id="word"></p>
</template>