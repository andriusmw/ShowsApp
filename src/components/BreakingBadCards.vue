<script setup>
    import axios from "axios"

const response = await axios.get("https://breakingbadapi.com/api/characters")
// specify the base url inside coloms + characters to get all characters
console.log(response)
</script>



<template>
    <div>
        <h1>  Breaking Bard cards </h1>
        {{response}}
    </div>
</template>