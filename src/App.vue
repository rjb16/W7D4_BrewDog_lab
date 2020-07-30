<template>
  <div>
    <h1>BrewDog Beers</h1>
    <beer-list></beer-list>
    <favourite-beers></favourite-beers>
    <beer-detail></beer-detail>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';
import BeerDetail from './components/BeerDetail.vue';

export default {


  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  }


}
</script>

<style>

</style>