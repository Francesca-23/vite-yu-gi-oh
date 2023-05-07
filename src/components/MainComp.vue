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

        <select name="cards" id="">
            <option value="Alien">Alien</option>
            <option value="Other">Other</option>
        </select>

        <div class="container">
            <div class="cards-number">
                <p>Found {{ store.array.length }} cards</p>
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

        select{
            padding: 0.5rem 0;
            padding-right: 3rem;
            background-color: white;
            border-radius: 5px;
            cursor: pointer;
            margin-bottom: 1rem;
            margin-left: 5rem;
        }
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
                display: flex;
                flex-wrap: wrap;
                gap: 1rem;
    
            }
        }
    }

</style>