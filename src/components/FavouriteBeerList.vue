<template lang="html">
  <div id="favourite_beers">
      <h2>Favourite Beers</h2>
      <ul>
          <li v-for="favouriteBeer in favouriteBeers">
              {{favouriteBeer.name}} 
              <img class="small-beer" :src="favouriteBeer.image_url"/>
              <button v-on:click="deleteFromFavourites" v-model="beerToBeDeleted">Delete</button> 
          </li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'favourite-beer-list',
    data(){
        return {
            beerToBeDeleted: {}
        }
    },
    props: ['favouriteBeers'],
    methods: {
        deleteFromFavourites() {
            const index = this.favouriteBeers.indexOf(this.beerToBeDeleted);
            this.favouriteBeers.splice(index, 1) 
        }
    }
}
</script>

<style>
.small-beer {
    height: 100px
}
</style>