<template>
  <div v-if='beer'>
      <h2> {{beer.name}} </h2>
      <p> ABV: {{beer.abv}}% </p>
      <p> Description: {{beer.description}} </p>
      <!-- <p> Food Pairings: </p>
      <ul>
          <li v-for="food in beer_food>{{food}}</li>
      </ul> -->
  </div>
</template>

<script>
export default {
    name: 'beer-detail',
    props: ['beer']
}
</script>

<style>

</style>