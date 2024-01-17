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

<!-- ------------------------------------- README ---------------------------------------
Originally we wanted to use more slots but it happens the Marvel's Api images are built using an object
which has the path and the extension separated, so in order to make it work we had to pass those properties
to the child component and then build the src route here on this component.

As you can see that suposse a problem cause we already have a cover image so in order to make things work
we used the v-if v-else directive so we can check the properties image which is the one we will receive when this
card component is called by the Rick and Morty component and show the correct image and if we do not receive it,
it means this component is being called by the Marvel's Component ( Breaking bad originally) and we render the 
ohter image. 

Note: in order to indicate VueJs that the src of the img tag is going to use a variable, we have to put : before src
example: <img :src="variable" alt="MyImageName">
-->