<script setup>
import { computed } from "Vue";
defineProps(["word", "guessedLetters"]);

/*
1. Wort wird zum Array
2. An diesem Array wird Array.map() aufgerufen. Diese wendet eine übergebene Funktion auf das Array an und erzeugt daraus ein neues Array
3. Array.map(letter =>) Letter ist das aktuelle Element des Array. Da es in der Arrow Function links von => ist, ist es der Parameter der Arrow Function
4. Jeder Letter: if(guessedletters.includes(letter) {return letter;} {return "_"})
5. .join(" "): Hänge ein Leerzeichen hinten dran

Fazit: Ich habe die Funktion map(). Dieser Funktion übergebe ich noch eine Funktion Parameter dieser Funktion sind die Elemente meines Arrays.
*/
const displayWord = computed(() => {
    return Array.from(props.word)
        .map(letter =>
            props.guessedLetters.includes(letter) ? letter : "_"
        )
        .join(" ");
});
</script>
<template>
    <p id="word">{{ displayWord }}</p>
</template>