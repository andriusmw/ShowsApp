<script setup>
    import axios from "axios"
    import { ref, watch } from "vue"
    const characters = ref(null)
    const page = ref(0)

const response = await axios.get("https://breakingbadapi.com/api/characters?limit=8")
// specify the base url inside coloms + characters to get all characters
characters.value = response.data
//console.log(response)

watch(page, async () => {
    const res = await axios.get(`https://breakingbadapi.com/api/characters?limit=8&offset=8&offset=${page.value * 8}`);
    characters.value = res.data
    //console.log(res)

} )


</script>



<template>
    <div>
        <h1>  Breaking Bard cards </h1>
        {{characters}}
        <div>
            <button @click="page = page++">Next</button>
            <button @click="page = page--">Back</button>
        </div>
    </div>
</template>