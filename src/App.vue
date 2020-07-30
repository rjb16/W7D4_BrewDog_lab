<template>
  <div>
    <h1>BrewDog Beers</h1>
    <beer-list :beers="beers"></beer-list>
    <favourite-beers></favourite-beers>
    <beer-detail></beer-detail>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';
import BeerDetail from './components/BeerDetail.vue';

export default {

  data(){
    return {
      beers: []
    }
  },



  mounted(){
        fetch("https://api.punkapi.com/v2/beers")
        .then(response => response.json()) 
        .then(data => this.beers = data)

    },


  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  }


}
</script>

<style>

</style>