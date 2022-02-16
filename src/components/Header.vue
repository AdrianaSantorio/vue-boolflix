<template>
  <header>
      <!-- barra di ricerca -->
      <Search  placeholder="Cerca un film" @search="emitSearch" />
  </header>
</template>

<script>

import Search from "./Search.vue";

export default {
    name:"Header",
    components: {
        Search, 
    },
    methods: {
        emitSearch(searchString) {
            this.$emit("search", searchString);
        }
    }
}
</script>

<style>

</style>