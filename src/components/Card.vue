<script setup>
    import{defineProps} from "vue"


    const {image, name} = defineProps([
        'image',
        'name'
    
  
    ])
</script>


<template>
    <NCard> 
        <template #cover>
            <img :src="image" alt="noImage">
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