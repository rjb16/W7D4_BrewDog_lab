<template>
  <div v-if="beer">
      <ul>
          <li>{{beer.name}}</li>
          <li>{{beer.abv}}</li>
          <li>
            <ul>
              <li v-for="(pairing, index) in beer.food_pairing" :key="index">{{pairing}}</li>
            </ul>
          </li>
      </ul>
      <button v-on:click="handleClick" type="submit">Add to favourites</button>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: "beer-detail",
    props: ['beer'],
    methods: {
      handleClick() {
        eventBus.$emit("favourite-beer", this.beer);
      }
    },
}
</script>

<style>

</style>