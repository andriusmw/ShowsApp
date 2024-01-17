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
        <KeepAlive>
         <BreakingBadCards v-if="isBreakingBad" />
         <RickMortyCards v-else />
       </KeepAlive>

      <!-- an example using the IS directive
         <KeepAlive>
           <Component :is="isBreakingBad ? BreakingBadCards : RickMortyCards" />
         </KeepAlive>
      -->


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
