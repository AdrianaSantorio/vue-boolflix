<template>
  <div id="app">
    <Header @search="logSearchString" />
    <Main />
  </div>
</template>

<script>

import Main from "./components/Main.vue";
import Header from "./components/Header.vue";


export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data() {
    return {
      searchString:"",
    }
  },
  methods: {
    logSearchString(searchString) {
      this.searchString = searchString;
      console.log(this.searchString);
    }
  }
}
</script>

<style lang="scss">
@import "./assets/sass/style.scss";
</style>
