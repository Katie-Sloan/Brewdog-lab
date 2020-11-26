<template>
  <div v-if='beer'>
      <h2> {{beer.name}} </h2>
      <p> ABV: {{beer.abv}}% </p>
      <p> Description: {{beer.description}} </p>
      <p> Ingredients: </p>
      <p> Malt: </p>
      <li v-for="ingredient in beer.ingredients.malt">
          {{ingredient.name}}
          ({{ingredient.amount.value}}
          {{ingredient.amount.unit}})
      </li>
      <p> Hops: </p>
      <li v-for="ingredient in beer.ingredients.hops">
          {{ingredient.name}}
          ({{ingredient.amount.value}}
          {{ingredient.amount.unit}})
          <ul>
            <li> When to add: {{ingredient.add}} </li>
            <li> Attribute: {{ingredient.attribute}} </li>
          </ul>
      </li>
      <p> Yeast: </p>
      <p> {{beer.ingredients.yeast}} </p>
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