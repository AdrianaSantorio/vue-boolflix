<template>
  <div id="app">
    <Header @search="searchMovies" />
    <Main :movies="movies"/>
  </div>
</template>

<script>

import axios from "axios";
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
      movies: [],
      api: {
        language: 'it-IT',
        baseUri: 'https://api.themoviedb.org/3',
        key: 'cad0f98a9a0e524439d751a1266b68c3',
      },
    }
  },
  methods: {
    searchMovies(searchString) {
      if(!searchString) {
        this.movies = [];
        return;
      }

      const {key, baseUri, language} = this.api;

      const config = {
        params: {
          api_key: key,
          query: searchString,
          language,
          }
      };

      axios.get(`${baseUri}/search/movie`, config).then(res => {
                
        this.movies = res.data.results;
        
        }).catch(err => {
                console.log(err);
        });


        }
  }
}
</script>

<style lang="scss">
@import "./assets/sass/style.scss";
</style>
