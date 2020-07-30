<template>
  
  <ul>
    <li v-for="(beer, index) in beers" :key="index">{{beer.name}}</li>
    
  </ul>
</template>

<script>
export default {
    name: "favourite-beers",
    props: ["beers"]

}
</script>

<style>

</style>