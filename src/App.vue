<script setup>
import BreakingBadCards from "./components/BreakingBadCardsSuspense.vue"
import RickMortyCards from "./components/RickMortyCards.vue"
import Hero from "./components/Hero.vue"
import {ref} from "vue"


const isBreakingBad = ref(true)
</script>

<template>
    <main>
      <Hero 
        :isBreakingBad="isBreakingBad"
        @selectShow="isBreakingBad = !isBreakingBad"
        ></Hero>
 <BreakingBadCards v-if="isBreakingBad" />
  <RickMortyCards v-else />

 
    </main>
</template>





<style scoped>
.cards {
  height: 700px;
  background-color: rgb(27,26,26);
  display: flex;
  justify-content: center;
  align-items: center;

}

</style>
