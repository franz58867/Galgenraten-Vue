<script setup>
import { computed } from "vue";
const props = defineProps(["mistakes"]);


const hangmanImage = computed(() => {
    if (props.mistakes <= 1) {
        return "images/0.jpg";
    }

    return "images/" + (props.mistakes - 1) + ".jpg";
})

</script>

<template>
    <img :src="hangmanImage">
</template>