<script setup>
    import axios from "axios"
    import { ref, watch, onMounted, onUpdated, onUnmounted, onBeforeMount } from "vue"
    import Card from "./Card.vue"

const page = ref(0)

// these are Hooks that active each time our app does certain things in its life cycle
onMounted(() => {
    console.log("Component is mounted")
})

// onUpdated is equal than watch but for all the app, not only an specific item
onUpdated(() => {
      console.log("Component was updated")
      // it needs to be rendered to apply its effect
})


onUnmounted(() => {
     console.log("Component was Unmounted")
})


onBeforeMount(() => {
    console.log("Component is about to mount")
})

</script>



<template>
   <div class="container">
    <!--
     <div class="button-container">
            <button @click="page--">Back</button>
            <button @click="page++">Next</button>
           
        </div>
         -->
        <div class="cards">
            <!--
            <Card 
            v-for="character in characters"
            :key="character.id"
            :image="character.image"
            :name="character.name"
            :occupation="character.occupation"
            :species="character.species"
            :location="character.location.name"
            />
            -->
        </div>
        
       
   </div>




</template>

<style scoped>
    /* Breaking Bad Styles */

.container {
    background-color: rgb(27, 26, 26);
    padding: 30px;
    margin-top: 100px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 700px
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}
.jobs {
    display: flex;
    flex-wrap: wrap;
}
.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>

<!-- ----------------------README ---------------------------

theorically this part would have been about an api from Breaking Bad,
however the api was down at the time of this project so i used a different
one from Rick & Morty, that was the second part. 

As a result some of the code is comment cause it was inttended to 
the breaking bad app but due to the different endpoints in each api
it doesn't work with this api, so there can be some parts of the
code were things are not 100% accurate, like pagination, this api
for the moment can only be paginated 20 elements at time but the
template was inttented to have only 8 per page so i had to put the
pagination buttons on top in order to be accesible. 

I hope i can fix it on the next version of the project when we
use the Rick and Morty api. 
-->