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
        <p class="card-name">{{ singleCard.name }}</p>
        <p class="card-type">{{ singleCard.archetype }} </p>
    </div>

</template>

<style scoped lang="scss">

    .card{
        width: calc(100% / 5 - 1rem);
        background-color: #d48f38;
        margin-bottom: 1rem;
        text-align: center;

        img{
            height: 20rem;
            width: 100%;
            object-fit: cover;
        }

        .card-name{
            text-transform: uppercase;
            color: white;
            font-weight: bold;
            padding: 1rem 0.5rem;
            font-size: 0.8rem;
        }

        .card-type{
            padding-bottom: 0.7rem;
        }
    }

</style>