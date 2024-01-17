<script setup>
    import{defineProps} from "vue"



    const {imagePath, name, imageExt, image} = defineProps([
        'imagePath',
        'name',
        'imageExt',
        'image'

    
  
    ])

const imgFull =`${imagePath}.${imageExt}`
//console.log(imgFull)
</script>


<template>
    <NCard> 
        <template #cover v-if="image !== undefined ">
            <img :src="image" alt="noImage">
        </template>

        <template #cover v-else>
            <img :src="imgFull" alt="noImagePath" >
        </template>
      <h3>{{name}}</h3>
   
        <slot>
           
         <!--Inside the slot appears what is
          inside the component while called on rickmortycards.vue
        -->
        </slot>
     
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