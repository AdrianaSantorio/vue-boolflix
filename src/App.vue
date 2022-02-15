<template>
  <div id="app">
    <Header @search="search" />
    <Main :movies="movies" :series="series" />
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
      series: [],
      api: {
        language: 'it-IT',
        baseUri: 'https://api.themoviedb.org/3',
        key: 'cad0f98a9a0e524439d751a1266b68c3',
      },
    }
  },
  methods: {
    search(searchString) {
      if(!searchString) {
        this.movies = [];
        this.series = [];
        return;
      }

      const {key, language} = this.api;

      const config = {
        params: {
          api_key: key,
          query: searchString,
          language,
          },
      };

      this.fetchApi('search/movie', config, 'movies');
      this.fetchApi('search/tv', config, 'series');
    },
    
    fetchApi(endpoint, config, target) {
        axios.get(`${this.api.baseUri}/${endpoint}`, config).then(res => {
                
          this[target] = res.data.results;
        
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
