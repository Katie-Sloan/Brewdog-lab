<template lang="html">
    <div>
        <select v-on:change="handleSelect" v-model="selectedBeer">
            <option disabled value="">Select a beer</option>
            <option v-for="beer in beers" :value="beer">{{beer.name}}</option>
        </select>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: "beer-list",
    data(){
        return {
            selectedBeer: {},
        }
    },
    props: ["beers"],
    methods: {
        handleSelect(){
            eventBus.$emit('beer-selected', this.selectedBeer)
        }
    }
}
</script>

<style>

</style>