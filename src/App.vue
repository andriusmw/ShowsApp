<script setup>
import BreakingBadCards from "./components/BreakingBadCards.vue"
import RickMortyCards from "./components/RickMortyCards.vue"
import { ref, watch, onMounted, onUpdated, onUnmounted } from "vue"

const showRickMortyCards = ref(true)
</script>

<template>
    <main>
      <h1>Hero</h1>
  <Suspense>
    <template #default>
          <BreakingBadCards />
    </template>
    <template #fallback>
      <div>
        <p>Loading...</p>
      </div>
    </template>

  </Suspense>
  <RickMortyCards v-if="showRickMortyCards"/>
  <button @click="showRickMortyCards = !showRickMortyCards">toggle</button>
    </main>
</template>





<style scoped>

</style>
