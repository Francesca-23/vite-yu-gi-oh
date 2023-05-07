<script>

    import Cards from './Cards.vue';
    import axios, {isCancel, AxiosError} from 'axios';
    import {store} from '../store'

    export default{
        name: "MainComp",
        components: {
            Cards
        },

        data(){
            return {
                store
            }
        },

        created() {
            this.activeApi()
        },

        methods: {

            activeApi(){

                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=12&offset=1').then( (response) => {
                    const result = response.data.data
                    this.store.array = result
                })  
            },

        }
    }

</script>

<template>

    <div class="big-container">

        <div class="container">
            <div class="cards-number">
                <p>number cards</p>
            </div>
            <div class="cards">
                <Cards v-for="(element, index) in store.array" :key="index"
                :singleCard="element"/>
            </div>
        </div>

    </div>


</template>

<style scoped lang="scss">

    .big-container{
        background-color: #d48f38;
        padding: 2rem 0;
        .container{
            width: 90%;
            margin: auto;
            background-color: white;
            padding: 2rem;

            .cards-number{
                padding: 1rem;
                background-color: #212529;
                color: white;
            }
            .cards{
    
            }
        }
    }

</style>