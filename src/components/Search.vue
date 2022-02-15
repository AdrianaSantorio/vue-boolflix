<template>
  <div>
       <div>
            <input type="text" v-model="searchString" :placeholder="placeholder || 'Cerca...' ">
            <button type="button" @click="emitSearch">Cerca</button>
        </div>
  </div>
</template>

<script>
export default {
    name: 'Search',
    props: ["placeholder"],
    data() {
        return {
            searchString: "",
        }
    },
    methods: {
        emitSearch() {
            this.$emit("search", this.searchString);
        }
    }
}
</script>

<style>

</style>