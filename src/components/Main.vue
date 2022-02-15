<template>
  <main>
      
    
      <!-- cards -->
      <div id="movie-gallery">

      </div>
      <div id="series-gallery"></div>

  </main>
</template>

<script>

// import axios from "axios";
import axios from "axios";


export default {
    name:"Main",
    components: {
    },
    data() {
        return {
            movies: [],
            api: {
                language: 'it-IT',
                //ma io lo voglio in inglese, quindi controllare
                baseUri: 'https://api.themoviedb.org/3',
                key: 'cad0f98a9a0e524439d751a1266b68c3',

            }
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
        
    },
}
</script>

<style>

</style>