<script setup>
    import axios from "axios"
    import { ref, watch } from "vue"
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
    <div>
        <h1>  Rick and Morty Cards </h1>
        {{characters}}
        <div>
            <button @click="page++">Next</button>
            <button @click="page--">Back</button>
        </div>
    </div>
</template>