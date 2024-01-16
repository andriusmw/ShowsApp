<template>
    <NCard title="Card with Cover"> 
        <template #cover>
            <img src="" alt="noImage">
        </template>
        Card Content
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