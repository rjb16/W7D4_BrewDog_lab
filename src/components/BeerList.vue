<template>
  
  <div>
      <list-item></list-item>
  </div>
  
</template>

<script>
import ListItem from "./ListItem.vue"

export default {
    name: "beer-list",

    components: {
        "list-item": ListItem
    }


}
</script>

<style>

</style>