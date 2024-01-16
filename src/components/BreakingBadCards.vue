<script setup>
    import axios from "axios"
    import { ref, watch } from "vue"
    import Card from "./Card.vue"

    const characters = ref(null)
    const page = ref(1)

// const response = await axios.get("https://breakingbadapi.com/api/characters?limit=8")
// la api de breaking bad ya no funciona de modo que he tenido que adaptar el código a la api de rick y morty
const response = await axios.get("https://rickandmortyapi.com/api/character")

// specify the base url inside coloms + characters to get all characters
characters.value = response.data.results
 console.log("page = " + page.value)
console.log(response)

watch(page, async () => {
    const res = await axios.get(`https://rickandmortyapi.com/api/character/?page=${page.value}`);
    characters.value = res.data.results
    console.log("page = " + page.value)
    console.log(res)

} )


</script>



<template>
   <div class="container">
        <div class="cards">
            <Card />
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