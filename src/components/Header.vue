<template>
  <header class="d-flex justify-content-between align-items-center p-5">
      <h1>BOOLFLIX</h1>
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

<style scoped lang="scss">
    header {
        height: 100px;
        background-color: black;
    }

    h1 {
        color: red;
        font-size: 3rem;
    }

</style>