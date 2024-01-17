<script setup>
    import axios from "axios"
    import { ref, watch, onMounted} from "vue"
    import Card from "./Card.vue"

const characters = ref(null)
const page = ref(1)

onMounted(async () => {
    const response = await axios.get("https://rickandmortyapi.com/api/character")
    characters.value = response.data.results
})

watch(page, async () => {
    const res = await axios.get(`https://rickandmortyapi.com/api/character/?page=${page.value}`);
    characters.value = res.data.results
    //console.log("page = " + page.value)
   // console.log(res)

} )


</script>



<template>
   <div class="container">
    
     <div class="button-container">
            <button @click="page--">Back</button>
            <button @click="page++">Next</button>
           
        </div>
         
        <div class="cards">
         
            
            <Card 
            v-for="character in characters"
            :key="character.id"
            :image="character.image"
            :name="character.name"
        
            
            
            >
                <p>{{character.species}}</p>
                <p>{{character.location.name}}</p>
            </Card>
        
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