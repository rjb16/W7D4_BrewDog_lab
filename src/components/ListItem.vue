<template>
  <div>
    <input type="radio" :id="beer.id" :value="beer" name="beers" v-on:click="handleClick" />
    <label :for="beer.id">{{beer.name}}</label>
  </div>
</template>

<script>
import { eventBus } from "../main.js";

export default {
  name: "list-item",
  props: ["beer"],
  methods: {
    handleClick() {
      eventBus.$emit("selected-beer", this.beer);
    },
  },
};
</script>

<style>
</style>