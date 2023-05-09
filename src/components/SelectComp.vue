<script>

    import {store} from '../store';
    import axios, {isCancel, AxiosError} from 'axios';

    export default{
        name: "SelectComp",

        data(){
            return{
                store
            }
        },

        created(){
            this.archetypeApi()
        },

        methods: {

            archetypeApi(){
                axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then( (response) => {
                    const result = response.data
                    this.store.archetype = result
                })
            },
        },
    }

</script>

<template>

    <div>
        <select name="cards" v-model="store.selected" @change="$emit('filterCards')">
            <option v-for="(element, index) in store.archetype" :key="index" :value="element.archetype_name">{{ element.archetype_name }} </option>
        </select>
    </div>

</template>

<style scoped lang="scss">

        select{
            padding: 0.5rem 0;
            background-color: white;
            border-radius: 5px;
            cursor: pointer;
            margin-bottom: 1rem;
            margin-left: 5rem;
        }

</style>