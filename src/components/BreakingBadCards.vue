<script setup>
    import axios from "axios"
    import { ref, watch } from "vue"
    import Card from "./Card.vue"

    const characters = ref(null)
    const page = ref(1)

// const response = await axios.get("https://breakingbadapi.com/api/characters?limit=8")
// la api de breaking bad ya no funciona de modo que he tenido que adaptar el código a la api de Marvel
// Marvel: https://gateway.marvel.com:443/v1/public/characters?limit=8&offset=8&apikey=f64582fc15b9d7e10b1eec158cdfd229


// hash = md5(1+privateKey+publickKey) = 43c14736770223d2203582fc40f332cf
// private key is on my desktop it is not supossed to be shared however with this data it should work,
// if not, just register on the MarevelApi website so you get your own keys.

const baseURL = "https://gateway.marvel.com:443"
const apiKey = "f64582fc15b9d7e10b1eec158cdfd229"
const hash = "43c14736770223d2203582fc40f332cf"
const response = await 
    axios.get(`${baseURL}/v1/public/characters?limit=8&offset=8&ts=1&apikey=${apiKey}&hash=${hash}`)

// specify the base url inside coloms + characters to get all characters
characters.value = response.data.data.results
 //console.log("page = " + page.value)
console.log(characters)

watch(page, async () => {
    const res = await 
        axios.get(`${baseURL}/v1/public/characters?limit=8&offset=${page.value * 8}&ts=1&apikey=${apiKey}&hash=${hash}`);
    characters.value = res.data.data.results
   // console.log("page = " + page.value)
 console.log(characters)

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
            :name="character.name"
            :imagePath="character.thumbnail.path"
            :imageExt="character.thumbnail.extension"
          
            >
           

                <div class="jobs ">
                     <p v-for="(url) in character.urls" :key="url">
                          <b>{{url.type}}: </b> <a :href="url.url" target="_blank"> Link </a> 
                         
                    </p>
                   
                </div>
            </Card>
        </div>
        
       
   </div>




</template>

<style scoped>
    /* Breaking Bad Styles */

.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
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

.jobs p{
   margin-right: 50px;
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

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
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