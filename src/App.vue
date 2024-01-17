<script setup>
import BreakingBadCards from "./components/BreakingBadCards.vue"
import RickMortyCards from "./components/RickMortyCards.vue"


</script>

<template>
    <main>
      <h1>Hero</h1>
  <Suspense>
    <template #default>
          <BreakingBadCards />
    </template>
    <template #fallback>
     <div class="cards spinner">
        <NSpin size="large"></NSpin>
     </div>

    </template>

  </Suspense>
  <RickMortyCards />

 
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
