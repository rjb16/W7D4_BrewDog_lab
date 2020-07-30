<template>
  <div>
    <h1>BrewDog Beers</h1>
    <beer-list :beers="beers"></beer-list>
    <favourite-beers :beers="favouriteBeers"></favourite-beers>
    <beer-detail :beer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';
import BeerDetail from './components/BeerDetail.vue';
import {eventBus} from './main.js'

export default {

  data(){
    return {
      beers: [],
      selectedBeer: '',
      favouriteBeers: []
    };
  },

  mounted(){
    this.getBeer()
    
    eventBus.$on("selected-beer", (beer) => {
      this.selectedBeer = beer;
    });

    eventBus.$on("favourite-beer", (beer) => {
      this.favouriteBeers.push(beer);
    });

  },

  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  },
  methods: {
    getBeer: function() {
    fetch("https://api.punkapi.com/v2/beers")
      .then(response => response.json()) 
      .then(data => this.beers = data);
    }

  }

}
</script>

<style>

</style>