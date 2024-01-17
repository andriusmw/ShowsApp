<script setup>
import {defineProps, defineEmits} from "vue" 

const emit= defineEmits(["selectShow"])

const {isBreakingBad} = defineProps([
    'isBreakingBad'
])

const emitSelectedShow = () => {
    emit("selectShow")
}

</script>

<template>
    <div class="hero">
        <h1>{{isBreakingBad ? 'Marvel': 'Rick and Morty'}}</h1>
        <p @click="emitSelectedShow">{{isBreakingBad ? 'Rick and Morty': 'Marvel'}}</p>
    </div>
</template>

<style scoped>

/* Hero Styles */
.hero {
    height : 40vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    flex-direction: column
}
.hero img {
    position: absolute;
    height: 700px;
    opacity: 0.1;
}
.hero h1 {
    font-size: 100px;
    font-weight: bold;
}
.hero p {
   
    margin-top: 200px;
    position: absolute;
 /* for now cause i can not se it */

    cursor: pointer;
}

</style>