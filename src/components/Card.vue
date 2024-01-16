<script setup>
    import{defineProps} from "vue"


    const {image, name, occupation, species, location} = defineProps([
        'image',
        'name',
       'occupation',
       'species',
       'location'
    ])
</script>


<template>
    <NCard> 
        <template #cover>
            <img :src="image" alt="noImage">
        </template>
      <h3>{{name}}</h3>
      <p><b>Species: </b> {{species}}</p>
        <p><b>Location: </b>{{location}}</p>
        <div class="jobs">
             <p v-for="(job, index) in occupation" :key="job">
                 {{job}} <span v-if="index < occupation.length - 1" >, </span>
            </p>
        </div>
     
    </NCard>


</template>

<style scoped>
/* Card Styles */

.n-card {
    width: 200px;
    margin:10px 20px;
   
}
.n-card img {
    height: 250px
}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}
</style>