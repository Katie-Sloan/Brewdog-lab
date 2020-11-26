<template>
  <div>
    <h1>Brewdog Beers</h1>
      <beer-list :beers='beers'></beer-list>
      <beer-detail :beer='selectedBeer'></beer-detail>
      <favourite-beer-list :favouriteBeers='favouriteBeers'></favourite-beer-list>
    <button v-if="selectedBeer && !favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add to fave</button>
  </div>

</template>

<script>
import BeerList from './components/BeerList.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeerList from './components/FavouriteBeerList.vue';
import { eventBus } from './main.js';

export default {
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourite-beer-list": FavouriteBeerList
  },
  methods: {
    addToFavourites(){
      this.favouriteBeers.push(this.selectedBeer)
    }
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = data)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  }
}
</script>

<style>

</style>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
