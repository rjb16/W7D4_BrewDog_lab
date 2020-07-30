<template>
  <div>
    <h1>BrewDog Beers</h1>
    <div class="main-content">
      <beer-list class="content-box" :beers="beers"></beer-list>
      <beer-detail class="content-box" :beer="selectedBeer"></beer-detail>
      <favourite-beers class="content-box" :beers="favouriteBeers"></favourite-beers>
    </div>
  </div>
</template>

<script>
import BeerList from "./components/BeerList.vue";
import FavouriteBeers from "./components/FavouriteBeers.vue";
import BeerDetail from "./components/BeerDetail.vue";
import { eventBus } from "./main.js";

export default {
  data() {
    return {
      beers: [],
      selectedBeer: "",
      favouriteBeers: [],
    };
  },

  mounted() {
    this.getBeer();

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
    "favourite-beers": FavouriteBeers,
  },
  methods: {
    getBeer: function () {
      fetch("https://api.punkapi.com/v2/beers")
        .then((response) => response.json())
        .then((data) => (this.beers = data));
    },
  },
};
</script>

<style>
body {
  background-color: #2a3439;
  color: #90c2e7;
  font-family: "Red Rose", cursive;
}
ul {
  list-style-type: none;
  padding: 0;
}
.main-content {
  display: flex;
}

.content-box {
  width: 30%;
  margin-right: 10px;
}
</style>