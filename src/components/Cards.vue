<script>

    export default{
        name: "Cards",
        props: ['singleCard'],
    }

</script>

<template>
    
    <div class="card">    
        <img v-for="(element, index) in singleCard.card_images" :key="index"
        :src="element.image_url" alt="">
        <p>{{ singleCard.name }}</p>
        <p>{{ singleCard.archetype }} </p>
    </div>

</template>

<style scoped lang="scss">

    .card{
        img{
            height: 10rem;
        }
    }

</style>